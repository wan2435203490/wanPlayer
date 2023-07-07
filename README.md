# wanPlayer

> wanPlayer 是由wan二开的一款在线音乐播放器，具有音乐搜索、播放、歌词显示、播放历史、查看歌曲评论、wyy用户歌单播放同步等功能

模仿 QQ 音乐网页版界面，采用 `flexbox` 和 `position` 布局；<br />
wanPlayer 虽然是响应式，但主要以 PC 端为主，移动端只做相应适配；<br />
只做主流浏览器兼容（对 IE 说拜拜，想想以前做项目还要兼容 IE7 ，都是泪啊！！！）


## 免责声明

**本项目仅为前端练手项目，不存在也不提供任何音频存储和贩卖服务**<br />
**本项目仅为前端练手项目，不存在也不提供任何音频存储和贩卖服务**<br />
**本项目仅为前端练手项目，不存在也不提供任何音频存储和贩卖服务**

## 安装与使用

### 检查 node 版本

```sh
# 查看 node 版本，确保 node 版本高于 12 版本
node -v
```

### wanPlayer

```sh
# 下载 wanPlayer
git clone https://github.com/wan2435203490/wanPlayer

# 进入 wanPlayer 播放器目录
cd Vue-wanPlayer

# 安装依赖 推荐使用 pnpm
pnpm install
# 或者
npm install

# 本地运行 wanPlayer
npm run serve

# 编译打包
npm run build
```

### 后台 api 服务（本地开发）

[wyy音乐 NodeJS 版 API](https://binaryify.github.io/NeteaseCloudMusicApi)

```sh
# 下载 NeteaseCloudMusicApi
git clone --depth=1 https://github.com/Binaryify/NeteaseCloudMusicApi

# 进入 NeteaseCloudMusicApi 后台服务目录
cd NeteaseCloudMusicApi

# 安装依赖
npm install

# 运行后台 api 服务 访问 http://localhost:3000
node app.js
```

### 注意点

**运行 wanPlayer 后无法获取音乐请检查后台 `api` 服务是否启动(即控制台请求报 404)**<br />
**线上部署不是直接将整个项目丢到服务器，再去运行 `npm run serve` 命令**<br />
**项目打包前 `VUE_APP_BASE_API_URL` 必须改后台 `api` 服务地址为线上地址，不能是本地地址**

## 技术栈

- [Vue Cli](https://cli.vuejs.org/zh/) Vue 脚手架工具
- [Vue 2.x](https://v2.cn.vuejs.org/) 核心框架
- [Vue Router](https://router.vuejs.org/zh/) 页面路由
- [Vuex](https://vuex.vuejs.org/zh/) 状态管理
- ES6 （JavaScript 语言的下一代标准）
- Less（CSS 预处理器）
- Axios（网络请求）
- FastClick（解决移动端 300ms 点击延迟）

## 项目结构目录图（使用 tree 生成）

<details>
<summary>展开查看</summary>
<pre><code>
├── public                                          // 静态资源目录
│   └─index.html                                    // 入口 html 文件
├── screenshots                                     // 项目截图
├── src                                             // 项目源码目录
│   ├── api                                         // 数据交互目录
│   │   └── index.js                                // 获取数据
│   ├── assets                                      // 资源目录
│   │   └── background                              // 启动背景图目录
│   │   └── img                                     // 静态图片目录
│   ├── base                                        // 公共基础组件目录
│   │   ├── mm-dialog
│   │   │   └── mm-dialog.vue                       // 对话框组件
│   │   ├── mm-icon
│   │   │   └── mm-icon.vue                         // icon 组件
│   │   ├── mm-loading
│   │   │   └── mm-loading.vue                      // 加载动画组件
│   │   ├── mm-no-result
│   │   │   └── mm-no-result.vue                    // 暂无数据提示组件
│   │   ├── mm-progress
│   │   │   └── mm-progress.vue                     // 进度条拖动组件
│   │   └── mm-toast
│   │        ├── index.js                           // mm-toast 组件插件化配置
│   │        └── mm-toast.vue                       // 弹出层提示组件
│   ├── components                                  // 公共项目组件目录
│   │   ├── lyric
│   │   │   └── lyric                               // 歌词和封面组件
│   │   └── mm-header
│   │   │   └── mm-header.vue                       // 头部组件
│   │   ├── music-btn
│   │   │   └── music-btn.vue                       // 按钮组件
│   │   ├── music-list
│   │   │    └── music-list.vue                     // 列表组件
│   │   └── volume
│   │        └── volume.vue                         // 音量控制组件
│   ├── pages                                       // 页面组件目录
│   │   ├── comment
│   │   │   └── comment.vue                         // 评论
│   │   ├── details
│   │   │   └── details.vue                         // 排行榜详情
│   │   ├── historyList
│   │   │   └── historyList.vue                     // 我听过的（播放历史）
│   │   ├── playList
│   │   │   └── playList.vue                        // 正在播放
│   │   ├── search
│   │   │   └── search.vue                          // 搜索
│   │   ├── topList
│   │   │   └── topList.vue                         // 排行榜页面
│   │   ├── userList
│   │   │   └── userList.vue                        // 我的歌单
│   │   ├── wanPlayer.js                             // 播放器事相关件绑定
│   │   └── music.vue                               // 播放器主页面
│   ├── router
│   │   └── index.js                                // 路由配置
│   ├── store                                       // vuex 的状态管理
│   │   ├── actions.js                              // 配置 actions
│   │   ├── getters.js                              // 配置 getters
│   │   ├── index.js                                // 引用 vuex，创建 store
│   │   ├── mutation-types.js                       // 定义常量 mutations 名
│   │   ├── mutations.js                            // 配置 mutations
│   │   └── state.js                                // 配置 state
│   ├── styles                                      // 样式文件目录
│   │   ├── index.less                              // wanPlayer 相关基础样式
│   │   ├── mixin.less                              // 样式混合
│   │   ├── reset.less                              // 样式重置
│   │   └── var.less                                // 样式变量（字体大小、字体颜色、背景颜色）
│   ├── js                                          // 数据交互目录
│   │   ├── axios.js                                // axios 简单封装
│   │   ├── hack.js                                 // 修改 nextTick
│   │   ├── mixin.js                                // 组件混合
│   │   ├── song.js                                 // 数据处理
│   │   ├── storage.js                              // localStorage 配置
│   │   └── util.js                                 // 公用 js 方法
│   ├── App.vue                                     // 根组件
│   ├── config.js                                   // 配置文件（播放器默认配置、版本号等）
│   └── main.js                                     // 入口主文件
└── vue.config.js                                   // vue-cli 配置文件

</code></pre>

</details>

