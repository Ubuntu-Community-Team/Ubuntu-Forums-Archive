---
title: "upgrade to ubuntu from xp networking not working"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by Titus_Stumme on 2014-10-07
Hey i just upgraded to ubnutu from xp and my networking wont work. i have an old dell computer. if anybody could help me out that'd be great.

---

### Post by davit2 on 2014-10-07
Hi, 
would you put here output of this command
$ sudo NetworkManager start

---

### Post by Hadaka on 2014-10-07
Hi ,please post the output of..
```
lspci -nn | grep 0280
rfkill list all
lsmod | egrep 'wl|b43'
cat /etc/modprobe.d
cat /etc/modules
```
thanks

---

