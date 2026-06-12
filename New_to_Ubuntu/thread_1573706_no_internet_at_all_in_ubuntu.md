---
title: "no internet at all in ubuntu"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by agdsargeant on 2010-09-13
hi.
i recently installed 10.04 (64 bit) on my macbook pro (5,5). i dual-boot. with no problems, i booted into ubuntu several times. once, after suspending my computer, i rebooted into osx. when i returned to ubuntu, i had no internet connection at all; when i went to preferences-> network connections, nothing appeared. before, i had been using an ethernet cable, and it worked just fine. back in osx, there are no problems, so i'm convinced i must have accidentally disabled my connection while in ubuntu.

any help would be appreciated.

---

### Post by garvinrick4 on 2010-09-13
Look in upper right hand corner for network applet. right click to make sure you are enabled and click on to get your router.

In this code should give you your domain and isp. Put it in a terminal to check.

```
gedit /etc/resolv.conf
```

---

