# 免费上线指南（site/ 静态站）

本目录 `site/` 是一个可独立部署的静态网站（纯 HTML/CSS，无需服务器、无需数据库）。
以下是三条零成本上线路线，按推荐顺序排列。

---

## 方案 A：Cloudflare Pages（推荐）

优点：免费、全球 CDN（海外访问快）、支持绑定自定义域名、免费 HTTPS。

前置：一个 GitHub 账号 + 一个 Cloudflare 账号。

步骤：

1. 在 GitHub 新建一个空仓库（如 `novamotion-site`）。
2. 把本目录内容推上去（只推 `site/` 里的文件，`index.html` 必须在仓库根）：
   ```
   cd site
   git init
   git add .
   git commit -m "init site"
   git branch -M main
   git remote add origin https://github.com/<你的用户名>/novamotion-site.git
   git push -u origin main
   ```
3. 登录 Cloudflare 控制台 → 左侧「Workers & Pages」→「Create」→「Pages」→「Connect to Git」→ 选 GitHub 仓库。
4. 构建设置：Framework 选 `None`，Build command 留空，Output directory 填 `.`（或 `/`）。
5. 点「Save and Deploy」，约 1 分钟出站，得到一个 `xxxx.pages.dev` 地址。
6. （可选）在 Pages 项目里「Custom domains」绑定你自己的域名，自动配好 HTTPS。

---

## 方案 B：GitHub Pages（最简单）

只需 GitHub 账号，无需 Cloudflare。

1. 建仓库，推 `index.html` 到根目录（同上第 1-2 步）。
2. 仓库 → Settings → Pages → Source 选 `main` 分支 + 根目录 → Save。
3. 得到 `https://<用户名>.github.io/novamotion-site/` 地址。
4. 也可在 Settings 里绑定自定义域名。

缺点：国内/部分地区访问速度一般，但对海外用户足够。

---

## 方案 C：Vercel（免费，开发者常用）

1. 到 vercel.com 用 GitHub 登录。
2. 「New Project」→ 导入 GitHub 仓库 → 自动识别为静态站 → Deploy。
3. 得到 `xxx.vercel.app` 地址，可绑自定义域名。

---

## 后续：有了流量再上 WordPress

当前静态站用于「零成本验证内容」。等积累到稳定流量、需要会员付费/连载管理/动态数据库时，再按 `CHECKLIST.md` 的方案买服务器 + 装 WordPress（Init Manga / Madara 主题），把内容迁过去。届时域名不变，只换后端。
