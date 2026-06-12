---
title: "vpn killswitch"
date: 2019-10-30
forum: Networking &amp; Wireless
---

### Post by vans25 on 2019-10-30
Hi 
Looking fo help to correctly setup killswitch after I disconnect from nordvpn (linux app) ( for example if manually disconnected and forget about it or switching to different location etc. becouse killswitch dosn't work in that case/time)
Buildin "killswitch" automatically stops all internet traffic while the VPN connection suddenly fails But it doesn't work if you disconnected manually or connecting to next location (in linux).
While connected with vpn ,   nordvpn diable my ufw and seting own firewall (but for a time it's connected)


Generally the only way to connect internet must be through nordvpn.


How to do it?
Looking for guide how to do it properly

---

### Post by #&amp;thj^% on 2019-10-30
On the Nord Linux client, it also disables system-wide internet access if the VPN connection suddenly disconnects. You can enable the Kill Switch feature by typing: 
```
nordvpn set killswitch
``` 
on command. If you want to disable the Kill Switch, type 
```
nordvpn set killswitch off 
```
You can find the current status of the Kill Switch feature by typing: 
```
nordvpn settings 
```

---

