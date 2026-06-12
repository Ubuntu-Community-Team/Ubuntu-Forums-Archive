---
title: "[SOLVED] Can't detect wireless"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by cierin on 2008-12-23
I'm having a bit of trouble connecting to wireless. I'm not sure that my computers even finding it, since this happens:
```
$ sudo ifconfig wlan0 up && sudo iwlist wlan0 scan
SIOCSIFFLAGS: No such file or directory
```

My wireless card is  Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

When I try to the network connection at the top right of the screen to connect, using "Connect to other wireless networks", it won't connect, even when I put in all my information correctly.

I'm trying to figure this out, but I'm a complete linux newbie. This is all really fun to work on, learning all the commands, starting to understand my OS, even if it is frusterating sometimes. :)

Edit: because I can't spell.

---

### Post by newbee70 on 2008-12-23
> **cierin said:**
> I'm having a bit of trouble connecting to wireless. I'm not sure that my computers even finding it, since this happens:
```
$ sudo ifconfig wlan0 up && sudo iwlist wlan0 scan
SIOCSIFFLAGS: No such file or directory
```

My wireless card is  Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

When I try to the network connection at the top right of the screen to connect, using "Connect to other wireless networks", it won't connect, even when I put in all my information correctly.

I'm trying to figure this out, but I'm a complete linux newbie. This is all really fun to work on, learning all the commands, starting to understand my OS, even if it is frusterating sometimes. :)

Edit: because I can't spell.


did you go into system/administration/Hardware drivers and enable it?

then did you left click on your network icon and on the wireless network?

---

