git --amend

git checkout -b xxx origin/xxx

git commit -am "xxxxx"

git push review-xxxx

git merge --log --no-ff origin/线上分支


1.git pull
git pull = git fetch + git merge FETCH_HEAD 

git pull --rebase =  git fetch + git rebase FETCH_HEAD 
2.merge 和 rebase
现在我们有这样的两个分支,test和master，提交如下：

       D---E test
      /
 A---B---C---F--- master
在master执行git merge test,然后会得到如下结果：

       D--------E
      /          \
 A---B---C---F----G---   test, master
在master执行git rebase test，然后得到如下结果：

A---B---D---E---C‘---F‘---   test, master
merge操作会生成一个新的节点，之前的提交分开显示。
而rebase操作不会生成新的节点，是将两个分支融合成一个线性的提交。

3.rebase好处
想要更好的提交树，使用rebase操作会更好一点。
这样可以线性的看到每一次提交，并且没有增加提交节点。

merge 操作遇到冲突的时候，当前merge不能继续进行下去。手动修改冲突内容后，add 修改，commit 就可以了。

而rebase 操作的话，会中断rebase,同时会提示去解决冲突。
解决冲突后,将修改add后执行git rebase –continue继续操作，或者git rebase –skip忽略冲突。

作者：GabrielPanda
链接：https://www.jianshu.com/p/dc367c8dca8e
来源：简书
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。