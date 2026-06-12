---
title: "Bypass flaky airplane mode switch"
date: 2019-04-14
forum: Networking &amp; Wireless
---

### Post by ddrake99 on 2019-04-14
Hi,

I have Ubuntu 18.04 on an old Dell Lattitude laptop.  It has an airplane mode switch on the right side that is very sensitive.  It switches off the wifi at the lightest touch, which is annoying.  Instead of replacing the switch, I would like to solve this in software.  I almost always want the wifi turned on.  It would be great if it could be forced on via a script at startup, but if that is not possible, maybe there could be a kernel blacklist solution?  With wifi switch on, I get

```
rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
When the switch is off, the Hard blocked items change to 'no'.

Thanks!
Dow

---

