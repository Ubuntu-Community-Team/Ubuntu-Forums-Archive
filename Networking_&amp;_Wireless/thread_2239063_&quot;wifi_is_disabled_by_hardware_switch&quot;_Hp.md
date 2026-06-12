---
title: "&quot;wifi is disabled by hardware switch&quot; Hp G6"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by emilydoaks on 2014-08-11
Okay so this problem is occuring on an HP G series laptop from 2 years ago.

I have tried countless things from other forums of how to change it but none of them worked and lots of them were specific to the make of the computer.

The problem I am having is that fn+f12 turns on the wireless. When pressed, the light indicator should change from orange(off) to white (on). It does not though.

I tried going into the system bios, the oly option related to the matter was to make it so you don't have to hit FN when using the system controls. So that way just f12 should turn it on. It does not though.

I am completely inexperienced at fixing anything like this and could GREATLY use some help. I assume you probably need info from me but I may not know how to retrieve it or what you would need.

Thanks ahead of time.

---

### Post by chili555 on 2014-08-11
Please open a terminal Ctrl+Alt+t and run and post:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep wmi
```Thanks.

---

