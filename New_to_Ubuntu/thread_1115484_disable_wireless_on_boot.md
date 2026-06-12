---
title: "disable wireless on boot"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by tzcomwiz on 2009-04-03
I normally use ethernet and ubuntu starts wireless everytime on boot. Is there a way to set it so wireless does not autostart?

Thanks.

---

### Post by kevstar31 on 2009-04-03
update-rc.d net.wlan0 stop 80 0 1 2 3 4 5 6

---

### Post by jimreynold2nd on 2009-04-04
Doesn't right-clicking on the network manager icon and untick "Enable Wireless" work?

---

### Post by tzcomwiz on 2009-04-04
update-rc.d: /etc/init.d/net.wlan0: file does not exist. yes the interface is wlan0

Yes right clicking and unchecking the wireless works. But I don't want it to even start on boot. I want something like rc-update del net.wlan0 default as in gentoo.

---

