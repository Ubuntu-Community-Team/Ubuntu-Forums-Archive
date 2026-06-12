---
title: "NetworkManager redirecting all traffic over OpenVPN (2)"
date: 2021-10-06
forum: Networking &amp; Wireless
---

### Post by leonardoprc on 2021-10-06
It is possible to configure some directive in the .ovpn file that forces this configuration:

[HTML]
NetworkManager applet icon > VPN Connections > Configure VPN... > select VPN network > Edit > IPv4 Settings > Routes... > Check 'Use this connection only for resources on its network'
[/HTML]

...something that reflects in the NM config file : "never-default=true"

???

---

