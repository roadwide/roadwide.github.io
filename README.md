# 备份说明

```bash
git clone -b source git@github.com:roadwide/roadwide.github.io.git
```

如果是已经存在本地的不是新的clone，记得先git pull  

复制并替换6个文件（夹）到上一步克隆的文件夹内  

```bash
cp -r _config.yml themes source scaffolds package.json ../roadwide.github.io/
```

然后提交  

```bash
cd ../roadwide.github.io
git add .
git commit -m "backup"
git push
```

# 恢复环境

依次执行
```bash
hexo init blog
cd blog
npm install
npm install hexo-deployer-git --save
rm -rf _config.yml themes source scaffolds package.json
cd ..
git clone -b source git@github.com:roadwide/roadwide.github.io.git
cd roadwide.github.io
cp -r _config.yml themes source scaffolds package.json ../blog/
```

# 注意

1、安装git、nodejs以及hexo后还需要安装git部署程序

```bash
npm install hexo-deployer-git --save
```

2、需要删除themes\jacman文件夹下的.git才能将主题备份（显示隐藏文件）

解决办法：删除之前代码残留的.git ，转换文件夹位置     push 操作删除 远程分支残留空文件夹。再重新提交一遍

3、hexo init后会默认生成一篇hello world的文章，需要手动删除

# 文件说明

- _config.yml：站点的配置文件，需要备份；
- themes：主题文件夹，需要备份；
- source：博客文章的 .md 文件，需要备份；
- scaffolds：文章的模板，需要备份；
- package.json：安装包的名称，需要备份；
- .gitignore：限定在 push 时哪些文件可以忽略，需要备份；（没有改动可以不备份）
- .git：主题和站点都有，标志这是一个 git 项目，不需要备份；
- node_modules：是安装包的目录，在执行 npm install 的时候会重新生成，不需要备份；
- public：是 hexo g 生成的静态网页，不需要备份；
- .deploy_git：同上，hexo g 也会生成，不需要备份；
- db.json：文件，不需要备份。
