# 身份核验卡 H5 页面

## 文件说明

```
├── exam_card_h5.html          # 主页面（核心文件）
└── assets/
    ├── 11.png                 # 蓝色信息卡背景图
    ├── ScreenShot_2026-05-26_111203_565.png  # 人物照片
    ├── ScreenShot_2026-05-26_115606_167.png  # 通知栏喇叭图标
    └── 微信图片_20260526110222_1473_165.jpg  # 绿色头部背景图
```

## 使用方法

### 1. 部署到服务器

将整个文件夹上传到你的服务器（如 Nginx、阿里云 OSS、腾讯云 COS 等），用户通过 URL 访问 `exam_card_h5.html` 即可。

### 2. 在小程序中使用

使用小程序的 `<web-view>` 组件加载该 H5 页面：

```html
<web-view src="https://你的域名/exam_card_h5.html"></web-view>
```

> 注意：小程序 web-view 需要配置业务域名白名单。

### 3. 替换个人信息

#### 方式一：通过 URL 参数传参（推荐）

在 URL 后面拼接参数即可动态替换内容：

```
https://你的域名/exam_card_h5.html?name=张三&idNumber=330106199001011234&roomNumber=040&seatNumber=08&venue=杭州市第十四中学&examNumber=330106199001011234&subject=建设工程造价案例分析&verifyTime=2026-05-17%2014:00:00&photoUrl=https://example.com/photo.jpg
```

页面会自动读取 URL 参数并替换对应内容。

#### 方式二：通过 JavaScript 调用

在页面加载后调用 `updateCard()` 函数：

```js
updateCard({
  name: '张三',                    // 姓名
  idNumber: '330106199001011234', // 身份证号
  roomNumber: '040',              // 考场号
  seatNumber: '08',               // 座位号
  venue: '杭州市第十四中学',        // 考点名称
  examNumber: '330106199001011234', // 准考证号
  subject: '建设工程造价案例分析',   // 科目
  verifyTime: '2026年05月17日 14:00:00', // 认证时间
  noticeText: '完成身份核验后，凭手机的核验成功界面、准考证、有效身份证原件进入考场',
  title: '2026年度监理工程师考试',
  status: '身份核验成功',
  photoUrl: 'https://example.com/photo.jpg' // 人物照片URL
});
```

### 4. 可替换字段一览

| 字段 | 参数名 | 说明 | 示例 |
|------|--------|------|------|
| 姓名 | name | 显示在蓝色卡片左侧 | 张三 |
| 身份证号 | idNumber | 显示在姓名下方 | 330106199001011234 |
| 考场号 | roomNumber | 显示在蓝色卡片右侧 | 040 |
| 座位号 | seatNumber | 显示在考场号下方 | 08 |
| 考点名称 | venue | 底部考点详情第一行 | 杭州市第十四中学 |
| 准考证号 | examNumber | 底部考点详情第二行 | 330106199001011234 |
| 科目 | subject | 底部考点详情第三行 | 建设工程造价案例分析 |
| 认证时间 | verifyTime | 底部考点详情第四行 | 2026年05月17日 14:00:00 |
| 通知文字 | noticeText | 顶部通知栏文字 | 完成身份核验后... |
| 考试标题 | title | 照片下方标题 | 2026年度监理工程师考试 |
| 状态 | status | 对勾图标旁的状态文字 | 身份核验成功 |
| 人物照片 | photoUrl | 证件照片URL | https://example.com/photo.jpg |

## 特性

- 顶部时间自动获取当前系统时间，毫秒级实时更新
- 日期自动显示当天日期
- 414 x 768 比例，适配移动端
- 所有文字内容均可替换
- 照片支持远程 URL 替换

## 注意事项

- 所有资源文件（assets 目录下的图片）建议上传到 CDN 或保持相对路径不变
- 小程序 web-view 需要 HTTPS 域名
- 如需修改样式，直接编辑 `exam_card_h5.html` 中的 `<style>` 块
