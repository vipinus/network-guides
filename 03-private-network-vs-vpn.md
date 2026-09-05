# 03 · 私网（Tailscale）和 VPN 的区别，什么时候该用它

> 网站版（更长、含繁体与英文）：https://7d24hrs.com/zh-CN/guides/tailscale-mesh

私网栏目用的是 Tailscale：基于 WireGuard 的组网工具，蓝盾自己运行控制服务器，你用本站账号登录。它和 AnyConnect、OpenVPN 这类「连接型」VPN 不是一回事。

## 三个区别

| | 连接型 VPN（AnyConnect / OpenVPN / sing-box） | 私网（Tailscale） |
|---|---|---|
| 连接 | 每次点连接，掉线要重连 | 登录一次一直在线，换网络自动恢复 |
| 出口 | 连上就是全部流量走出口 | 出口可选：不选时公网流量走本地，只有私网内设备间的流量加密；选了某地区出口才等于 VPN |
| 设备互通 | 无 | 同一账号下的手机、电脑、NAS 互相能直接访问，不用端口映射和公网 IP |

## 该用它的情况

- 多设备、想一次配置永远在线。
- 家里有 NAS、电脑、摄像头要在外面访问：两边都登录私网，用设备名直连，像在局域网里。
- 需要长时间挂着的设备：没有会话超时。

## 不该用它的情况

- 只想临时用一次：扫码导入 sing-box 或装 AnyConnect 更快。
- 设备上已经跑着公司 VPN 或别的组网软件：两者争 DNS 和路由，症状是看国内视频提示版权、公司内网打不开。用网页代理这种只影响浏览器的方式。
- 校园网 / 公司网限制 UDP：WireGuard 走 UDP，只能靠中继，慢；换 AnyConnect。

## 到期和设备数

设备登录有效期跟账号到期日走，到期几分钟内离线，续费后重新登录即可。5 台同时在线与其他接入方式共用额度，超出踢最久没上线的。

安装与登录步骤见 [客户端指南 05](https://github.com/vipinus/client-guides/blob/main/05-tailscale-private-network.md)。

---
由 [蓝盾](https://7d24hrs.com) 团队整理 · 问题来 [Telegram 群](https://t.me/+NWJN_9yITj9kOWFh) · 注册领 24 小时免费试用，邀请朋友每位送 30 天，长期有效
