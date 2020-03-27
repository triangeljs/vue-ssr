### 什么是SSR

把Vue组件渲染为服务器端的HTML字符串，将他们直接发送到浏览器，最后将静态标记混合为客户端上完全交互的应用程序。

### 为什么要使用SSR

1.更好的SEO，搜索引擎爬虫爬取工具可以直接查看完全渲染的页面
2.更宽的内容达到时间（time-to-content），当权请求页面的时候，服务端渲染完数据之后，把渲染好的页面直接发送给浏览器，并进行渲染。浏览器只需要解析html不需要去解析js。

### SSR弊端

1.开发条件受限，Vue组件的某些生命周期钩子函数不能使用
2.开发环境基于Node.js
3.会造成服务端更多的负载。在Node.js中渲染完整的应用程序，显然会比仅仅提供静态文件server更加占用CPU资源，因此如果你在预料在高流量下使用，请准备响应的服务负载，并明智的采用缓存策略。

### 准备工作 & SSR渲染手动搭建

首先要创建一个项目，创建一个文件夹，名字不重要，但是最好不要使用中文

`
mkdir vue-ssr
cd vue-ssr
npm init
`

npm init命令用来初始化package.json文件

`
{
  "name": "dome",   //  项目名称
  "version": "1.0.0",   //  版本号
  "description": "",    //  描述
  "main": "index.js",   //  入口文件
  "scripts": {          //  命令行执行命令 如：npm run test
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Aaron",     //  作者
  "license": "ISC"      //  许可证
}
`

初始化完成之后接下来需要安装，项目所需要依赖的包，所有依赖项如下

`
npm install express
npm install vue
npm install vue-server-renderer
npm install vue-router
`

为了方便我们需要在package.json添加一个命令，方便后续开发启动项目

`
{
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index.js"
  }
}
`