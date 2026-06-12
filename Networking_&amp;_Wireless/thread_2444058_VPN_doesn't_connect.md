---
title: "VPN doesn't connect"
date: 2020-05-24
forum: Networking &amp; Wireless
---

### Post by mandarine2 on 2020-05-24
Hi,

I'm trying to connect a Laptop running Lubuntu 20.04 via VPN to a FritzBox using [this]("https://avm.de/service/vpn/tipps-tricks/vpn-verbindung-zur-fritzbox-unter-linux-einrichten/") manual. The connection does't work.

/**var/log/syslog**
shows

```
May 23 15:53:58 mycomputer NetworkManager[1754]: <info>   [1590242038.3886]  vpn-connection[0x559acc0d0360,0496231e-022d-4bd4-ba0f-xx,"VPN-Connection",0]:  Started the VPN service, PID 2457
May 23 15:53:58 mycomputer NetworkManager[1754]: <info>   [1590242038.4052]  vpn-connection[0x559acc0d0360,0496231e-022d-4bd4-ba0f-xx,"VPN-Connection",0]:  Saw the service appear; activating connection
May 23 15:53:58 mycomputer NetworkManager[1754]: <error>  [1590242038.4170]  vpn-connection[0x559acc0d0360,0496231e-022d-4bd4-ba0f-xx,"VPN-Connection",0]:  Failed to request VPN secrets #3: No agents were available for this  request.
May 23 15:53:58 mycomputer NetworkManager[1754]: <info>   [1590242038.4239]  vpn-connection[0x559acc0d0360,0496231e-022d-4bd4-ba0f-xx,"VPN-Connection",0]:  VPN plugin: state changed: stopped (6)
```

Everything I found on the Internet didn't help &#9785;

Regards
Sascha

---

