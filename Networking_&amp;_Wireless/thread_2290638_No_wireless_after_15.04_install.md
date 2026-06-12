---
title: "No wireless after 15.04 install"
date: 2015-08-13
forum: Networking &amp; Wireless
---

### Post by colmeweb on 2015-08-13
So I got a new Lenovo Edge 15 (Not the think pad) and I installed 15.04 on it. The wireless isn't showing up. I can't even see the wifi to turn it on and off.
I had this problem a few years ago, but that was a totally different machine so the same thing didn't work.

A little starter:
```
@Lenovo-Edge:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0041] (rev 20)
```

Thanks

---

### Post by Hadaka on 2015-08-14
Hi, It looks like your device is not supported.
[http://ubuntuforums.org/showthread.php?t=2290403](http://ubuntuforums.org/showthread.php?t=2290403)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1436940)
time to shop for a dongle.

---

### Post by colmeweb on 2015-08-15
Well hell, does anybody know of a way around this other than a cord or dongle?
Any brilliant coders out there that would like to write a quick driver :)

---

