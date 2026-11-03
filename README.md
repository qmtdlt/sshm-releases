# sshm 公共下载

sshm 是终端里的 SSH 连接管理器。本仓库只提供安装脚本与发布产物，不包含开发源码。

## Linux x64 一条命令安装

```sh
curl -fsSL https://raw.githubusercontent.com/qmtdlt/sshm-releases/main/install.sh | sh
```

需要 Linux x86_64、curl、OpenSSL 3+、tar/gzip 和 OpenSSH 客户端。默认安装到 `/usr/local/bin/sshm`，非 root 用户会按需请求 sudo 授权。安装后输入：

```sh
sshm
```

不具备 sudo 权限时，可指定已在 PATH 中的个人目录：

```sh
curl -fsSL https://raw.githubusercontent.com/qmtdlt/sshm-releases/main/install.sh | SSHM_INSTALL_DIR="$HOME/.local/bin" sh
```

脚本校验独立 Ed25519 签名及 SHA-256 后安装；不会修改连接记录、SSH 私钥或凭据。重复安装相同内容不会重写程序，损坏包会被拒绝；不会覆盖其他方式安装的 sshm。

当前提供 Linux x64 静态程序：Ubuntu 22.04、Alpine 3.24 完整安装已在容器验证；Debian 12、Rocky Linux 9 通过程序启动检查。不承诺旧 CentOS、旧内核或 Linux ARM64 兼容。从 v0.4.1 起支持远程登录：SSH 会话中按 g，或同步页面按 r，按屏幕说明在浏览器所在电脑建立 SSH 转发，再打开授权链接。Linux 可选择“记住登录”，无需 Secret Service，重启自动恢复；令牌不加密，以仅当前用户可读的文件保存，root 也可读取。退出登录会删除保存的令牌。真实账号授权及跨机同步仍需用户实测。

Linux 自动更新暂未提供；需要时可重新执行安装命令。仅卸载本脚本安装的程序、保留用户数据：

```sh
sudo rm /usr/local/bin/sshm /usr/local/bin/.sshm-install.sha256
```

遇到下载失败，请确认服务器能连接 GitHub 与 raw.githubusercontent.com。
