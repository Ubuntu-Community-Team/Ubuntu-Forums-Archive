---
title: "Gnome doesn't use my Socks Proxy, Mozilla does [Gutsy]"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by der_vegi on 2007-10-05
Okay, before I file a bug report, I'd like to know, if I am doing anything wrong:

I am using Gutsy Beta (all updates until Oct. 5th) and I am connected over wireless LAN and VPN to the internet. I also need a proxy for HTTP access, ports for POP are blocked. I use port 1080 as proxy by tunneling with
```
ssh -D 1080 user@host
```
to deal with emails. That works fine with Thunderbird and I also successfully tried to use it in Firefox. But when I set the socks proxy (localhost, 1080) in Gnome over System => Settings => Network-Proxy, it doesn't work. I cannot connect to my email account using Evolution and apt can't connect either. Setting the Proxy of my university-network (which is a http proxy) works for apt, but not for Evolution, as the ports are blocked. What am I doing wrong?

Thanks for the help!

---

### Post by chefweb on 2007-10-07
I have the same problem like you. I think evolution is not able to use socks! .. I hope the developers will include this in future..

---

### Post by der_vegi on 2007-10-07
Well, is apt also incapable of using socks? Because apt doesn't work for me with socks either, but with the other http-proxy. Maybe it is a bug, so I have filed a bug report, see
[launchpad bug # 149728]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/149728").

---

