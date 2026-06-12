---
title: "ubuntu 14.04 on Toshiba wifi not working"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by Bryant_Arrington on 2014-04-19
[CODElaptop@laptop-Satellite-A205:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
laptop@laptop-Satellite-A205:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
laptop@laptop-Satellite-A205:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
][/CODE]

I can't figure out how to fix blocks.

---

### Post by tfrue on 2014-04-19
try:
 ```
sudo rfkill unblock all
```

---

