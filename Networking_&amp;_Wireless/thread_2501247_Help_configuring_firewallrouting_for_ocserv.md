---
title: "Help configuring firewall/routing for ocserv"
date: 2024-09-29
forum: Networking &amp; Wireless
---

### Post by anebotov on 2024-09-29
[COLOR=#0C0D0E][FONT=-apple-system]I installed ocserv (ver 1.3.0) But when [/FONT][/COLOR][COLOR=#0C0D0E][FONT=-apple-system]connecting access via OpenConnect there is no internet.

[/FONT][/COLOR]On VPS with [COLOR=#0C0D0E][FONT=-apple-system]ocserv:[/FONT][/COLOR]  

[LIST]
[*]change /etc/ufw/before.rules
[/LIST]
-A ufw-before-forward -s 192.168.2.0/24 -j ACCEPT
-A ufw-before-forward -d 192.168.2.0/24 -j ACCEPT
-A ufw-before-forward -s 192.168.3.0/24 -j ACCEPT
-A ufw-before-forward -d 192.168.3.0/24 -j ACCEPT
...
*nat
:POSTROUTING ACCEPT [0:0]
-A POSTROUTING -s 192.168.2.0/24 -o eth0 -j MASQUERADE

[LIST]
[*]change /etc/default/ufw
[/LIST]
DEFAULT_OUTPUT_POLICY="ACCEPT"

[LIST]
[*]change /etc/sysctl.conf
[/LIST]
net.ipv4.ip_forward = 1
net.core.default_qdisc = fq
net.ipv4.tcp_congestion_control = bbr

What else do i need to do?

---

