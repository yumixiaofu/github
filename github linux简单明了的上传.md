# 注意事项

git remote add origin https://github.com/BlueYuQuan/test.git 这里别忘了把origin换成自己仓库的名字，还有https链接也要换


git push -u origin master，这里别忘记把origin换成仓库的名字，master是版本，自己随意测试



# 如何将linux下的代码上传到github上

本文适用情景：linux系统，第一次上传，远端没有对应厂库。其它情景仅作参考！
1.安装git
首先，你可以试着输入 'git'，看看系统有没有安装Git：

$ git
The program 'git' is currently not installed. You can install it by typing:
如果没有，则安装

$ sudo apt-get install git
2.初始化配置
如果想长期在某台设备上使用git,则建议配置一下，如果仅仅就是一次，请忽略！

$ git config --global user.name XXXX（你的github用户名）
$ git config --global user.email XXXX（你的github的email）
3.指定代码厂库（repository）
代码厂库可以理解为一个文件夹，里面存放我们需要管理或上传的代码 如果你已经明确要上传哪个文件夹下的代码文件，则==cd==进该文件夹==此处假定文件夹名为test==

$ cd XXX/test
如果没有明确的文件夹，则建立并==cd==进入

$ mkdir XXX/test
将该文件夹初始化为真实的代码厂库：

$ git init
也可以合并以上内容直接穿件一个空的git厂库

$ git init test
初始化空的 Git 仓库于 /home/test/.git/
此时该文件夹下会生成一个隐藏的 ==.git==文件，可以通过 ==ls -ah==查看

$  ls -ah
.  ..  .git

4.将需要上传的文件代码加入到厂库中
一下命令意为将当前==test==目录下的所有文件加入到厂库缓存区==.get==中

git add .
==如果只是想将单个或某些文件添加，那么将‘.’号换成需要添加的文件名==

5.commit提交
git commit -m '本次提交的注释'
6.在远端github上创建远程库
在你的github上创建一个和本地厂库同名的（==test==）厂库 输入图片说明 输入图片说明 输入图片说明

7.将本地厂库于远程库相关联
$ git remote add origin https://github.com/BlueYuQuan/test.git
将其中的==BlueYuQuan==换成你的github用户名。 添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的。

8.推送本地库内容到远端库
$ git push -u origin master
之后可能要你输入git的用户名和密码，没有错误的话输入即可完成！

把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。

由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

9 验证
本地库上我写了两个文件==Readme.md==和==test.txt==

$ l
Readme.md  test.txt
查看远端库

输入图片说明

成功！

从现在起，只要本地作了修改并提交，就可以通过命令：

$ git push origin master
把本地master分支的最新修改推送至GitHub！

10.可能遇到的问题
1.推送代码时报错，如下;
$  git push -u origin master
error: src refspec master does not match any.
error: 无法推送一些引用到 'https://github.com/BlueYuQuan/test.git'
原因：本地仓库为空，没有添加文件，git默认空文件夹不上传；或者没有commit注释

声明！以上内容纯属个人经验！如果有帮助到你，希望能动动小手点个赞。 如有错误请多指正！如有雷同！纯属巧合！





# 参考资料
https://my.oschina.net/blueyuquan/blog/1587079
