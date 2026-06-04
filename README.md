# 砚 · 推免申请材料工作台

> 基于 [Gloria040510/Yan](https://github.com/Gloria040510/Yan) 的个人定制版

推免申请材料工作台。把通知、材料、档案、缺漏检查与导出整理到一处。

## 主要改动

### 1. AI 解析优化
- 接入 **小米 MiMo API**（mimo-v2.5 模型）
- AI 解析超时时间从 30 秒增加到 **5 分钟**
- 解析失败时显示加载状态提示（⏳ 正在解析中...）
- 解析完成根据 AI/本地规则显示不同提示

### 2. 热点资讯模块扩充
原项目仅有科技热点，现扩充为三个板块：

| 板块 | 数据源 | 内容 |
|------|--------|------|
| 科技资讯 | 量子位、机器之心 | AI Agent、大模型、具身智能等 |
| 时事热点 | 人民网 RSS | 政策法规、国际关系、教育科技等 |
| 经济金融 | 新浪财经 API | 股市、货币政策、国际贸易等 |

- 顶部 Tab 切换：科技资讯 | 时事热点 | 经济金融
- 自动过滤无关社会新闻（八卦、娱乐等）
- 时事/经济新闻保留真实摘要

### 3. 手动编辑功能
- 支持手动编辑解析后的**学院**字段
- 点击即可修改，按 Enter 自动保存

## 快速开始

```bash
# 安装依赖
npm install

# 配置本地设置
cp config/app.example.json config/app.local.json

# 编辑 config/app.local.json，填入你的信息和 API Key

# 启动服务
npm run dev
```

打开 http://localhost:5178

## 配置文件

编辑 `config/app.local.json`：

```json
{
  "ai": {
    "provider": "openai-compatible",
    "baseUrl": "https://token-plan-cn.xiaomimimo.com/v1",
    "apiKey": "你的小米MiMo API Key",
    "model": "mimo-v2.5"
  },
  "profile": {
    "name": "你的姓名",
    "homeUniversity": "你的本科学校",
    "major": "你的专业",
    "targetMajor": "申请方向"
  }
}
```

## 技术栈

- **Runtime**: Node.js 20+
- **Backend**: Node 原生 HTTP server
- **Frontend**: 原生 HTML / CSS / JavaScript SPA
- **AI**: 小米 MiMo API（OpenAI 兼容格式）
- **Storage**: 本地 JSON

## License

MIT
