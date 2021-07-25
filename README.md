<!--
 * @Author: xiaoping.xu
 * @Date: 2021-07-24 01:06:34
 * @LastEditors: xiaoping.xu
 * @LastEditTime: 2021-07-25 01:23:10
 * @Desc:
-->

# cli

1、npm init 初始化 npm 项目

2、执行 lerna init  
结果  
lerna notice cli v4.0.0  
lerna info Creating package.json  
lerna info Creating lerna.json  
lerna info Creating packages directory  
lerna success Initialized Lerna files

3、yarn

4、新建.gitignore 文件

5、lerna create core
lerna create utils

6、安装/卸载依赖
lerna add lodash 在所有包中安装依赖
lerna clean 卸载所有包中的所有依赖

192:lernaDemo xuxiaoping$ lerna add lodash
info cli using local version of lerna
lerna notice cli v4.0.0
lerna info Adding lodash in 2 packages
lerna info Bootstrapping 2 packages
lerna info Installing external dependencies
lerna info Symlinking packages and binaries
lerna success Bootstrapped 2 packages

192:lernaDemo xuxiaoping$ lerna clean
info cli using local version of lerna
lerna notice cli v4.0.0
lerna info Removing the following directories:
lerna info clean packages/core/node_modules
lerna info clean packages/utils/node_modules
? Proceed? Yes
lerna info clean removing /Users/xuxiaoping/work/未命名文件夹 2/webDesign/code/lernaDemo/packages/core/node_modules
lerna info clean removing /Users/xuxiaoping/work/未命名文件夹 2/webDesign/code/lernaDemo/packages/utils/node_modules
lerna success clean finished

192:lernaDemo xuxiaoping$ lerna add lodash packages/core/
info cli using local version of lerna
lerna notice cli v4.0.0
lerna WARN No packages found where lodash can be added.
这里的 warn，需要手动删除包中 package.json 中的依赖

lerna add lodash packages/core/ 在 core 包中安装 lodash
lerna add -h 查看帮助

如何引用本地包
步骤一、在 package.json 的 dependencies 中手动添加依赖包及其版本
步骤二、lerna link
步骤三： 查看软链接指向
192:lernaDemo xuxiaoping$ cd packages/core/
192:core xuxiaoping$ cd node_modules
192:node_modules xuxiaoping$ cd @xuxiaoping2018
192:@xuxiaoping2018 xuxiaoping$ ls -l
total 8
lrwxr-xr-x 1 xuxiaoping staff 14 7 25 01:10 imooctest-utils -> ../../../utils
这里的软链接指向了本地

lerna exec 命令 在所有包下执行某条命令，例如删除所有包下的 node_modules
lerna exec -- rm -rf node_modules
info cli using local version of lerna
lerna notice cli v4.0.0
lerna info Executing command in 2 packages: "rm -rf node_modules"
lerna success exec Executed command in 2 packages: "rm -rf node_modules"
