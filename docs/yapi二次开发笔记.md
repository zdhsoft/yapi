# 二次开发笔记
## 运行
```javascript
{
  "scripts": {
    "dev-copy-icon": "cp -r static/iconfont ./",
    "dev-server": " nodemon server/app.js dev -L",
    "install-server": " node server/install.js",
    "dev-client": "npm run dev-copy-icon && ykit s -p 4000",
    "dev": "npm run dev-server & npm run dev-client",
    "start": " node server/app.js",
    "test": "ava",
    "build-client": "ykit pack -m NODE_ENV=production",
    "npm-publish": "node ./npm-publish.js",
    "docs": "ydoc build"
  },
  "scripts-info": {
    "start": "运行生产环境服务器",
    "install-server": "初始化数据库数据，用于安装",
    "dev": "运行开发服务器",
    "dev-server": "运行后端开发服务器",
    "dev-client": "运行前端开发服务器",
    "test": "执行测试"
  },
}
```
## 问与与修复
### 1、数据库用户名密码不正确
- 将server\utils\db.js中的dbconfig注释
```javascript
// 如果你的数据库，没有设置用户名和密码的时候
//   if (config.db.user) {
//     options.user = config.db.user;
//     options.pass = config.db.pass;
//   }
```
或者你配置一个用户名写密码
### 2、在windows环境下，连接数据库返回undefined
- 将 let db = mongoose.connect 中的db放弃使用, 使用const db =  mongoose.connection;获得db
```javascript
  //let db = await mongoose.connect(connURL, option);
  const db =  mongoose.connection;
```
