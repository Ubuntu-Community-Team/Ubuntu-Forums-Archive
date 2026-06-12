---
title: "Wifi default and Broadcom drivers not working"
date: 2015-03-05
forum: Networking &amp; Wireless
---

### Post by harrispartyof3 on 2015-03-05
Installed ubuntu on a Dell Inspiron from what I remember the wifi was working when using ubuntu via live usb. after installing the default driver doesn’t seem to work. after following some online guides I installed the Broadcom STA Wireless Driver, which also ended up not working. Are there any other drivers that have been known to work with ubuntu 14.04?

---

### Post by Hadaka on 2015-03-05
please post the output of..
```
lspci -n | grep 0280
```

---

### Post by harrispartyof3 on 2015-03-10
This is the output of lspci -n | grep 0280:
```
02:00.0 0280; 14e4:4365 (rev 01)
```

---

### Post by Hadaka on 2015-03-10
Hi,please try the link first, if you need additional help
let us know.
[http://ubuntuforums.org/showthread.php?t=2214110&](http://ubuntuforums.org/showthread.php?t=2214110&)
thanks.

---

### Post by redrach2 on 2015-04-06
00:0b.0 0280: 14e4:4318 (rev 02)

---

