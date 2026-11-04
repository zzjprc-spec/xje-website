# 馨尖环保 XJ 网站

这是一个不需要构建工具的单页静态网站，可直接部署到任意静态托管服务。

## 本地预览

在项目目录中启动任意静态文件服务器，例如：

```powershell
python -m http.server 8000
```

然后访问 `http://localhost:8000/`。

## 发布到 GitHub Pages 与 xjenviro.com

1. 在 GitHub 新建名为 `xje-website` 的空仓库，不要初始化 README。
2. 在项目目录执行：

```powershell
git init
git add index.html styles.css script.js README.md CNAME .nojekyll assets\xje-logo.png assets\xje-mark.png assets\vox-logo.png assets\ai-workflow-enhanced.jpg
git commit -m "Publish XJE website"
git branch -M main
git remote add origin https://github.com/GITHUB_USERNAME/xje-website.git
git push -u origin main
```

3. 打开仓库 `Settings → Pages`，将 Source 设为 `Deploy from a branch`，Branch 设为 `main`，目录设为 `/ (root)`。
4. 在 `Settings → Pages → Custom domain` 中填写 `xjenviro.com`。
5. 在域名服务商的 DNS 控制台配置：

```text
A     @      185.199.108.153
A     @      185.199.109.153
A     @      185.199.110.153
A     @      185.199.111.153
AAAA  @      2606:50c0:8000::153
AAAA  @      2606:50c0:8001::153
AAAA  @      2606:50c0:8002::153
AAAA  @      2606:50c0:8003::153
CNAME www    GITHUB_USERNAME.github.io
```

6. 如果 GitHub 显示域名验证 TXT 记录，按页面给出的 `_github-pages-challenge-...` 值添加记录。
7. 等待 DNS 生效，然后返回 GitHub Pages 勾选 `Enforce HTTPS`。

项目中的 `CNAME` 文件已经设置为 `xjenviro.com`。不要在 GitHub 上删除或修改它。

当前线上站点：`https://xjenviro.com/`，GitHub Pages 已开启强制 HTTPS。

## 上线前需要确认

- VOx Envirotech 已链接至 `https://www.voxenviro.com/`，共 3 处入口。
- 联系入口已设置为 `zzjprc@gmail.com`。
- 当前页面未放置电话号码、办公地址、备案号等真实信息；如有，可在联系区与页脚补充。

## 文件结构

- `index.html`：页面内容、SEO 与应用信息
- `styles.css`：响应式视觉样式
- `script.js`：移动导航、滚动显现与年份
- `assets/xje-logo.png`：用户提供的完整品牌标志
- `assets/xje-mark.png`：从原标志裁切的水波图形，用于页眉与能力模型
- `assets/vox-logo.png`：VOx Envirotech 官网使用的品牌标志
- `assets/ai-workflow-enhanced.jpg`：用户提供的人工智能辅助技术与业务主题图，已进行 2 倍无损插值和轻度锐化处理
