---
title: "USB-to-Serial cable recommendations"
date: 2016-09-11
forum: Networking &amp; Wireless
---

### Post by DrRus on 2016-09-11
So, I've been using USB-to-Serial cable from Tripplite (U209-000-R) to connect Windows machines to a console port on a switch/router.

I wanted to practice some networking with Ubuntu now, but lo and behold - the drivers from the Tripplite site apparently don't work with Ubuntu.

Anyone connecting to switches/routers console - could you recommend drivers (something that would work on Ubuntu) or a different cable altogether?

What's working for you?

Thanks

---

### Post by DrRus on 2016-09-11
It turned out that I didn't need drivers, after all, just had to change the permissions on /dev/ttyUSB0

Nice!

---

### Post by King of Heart 4711 on 2016-09-11
> **DrRus said:**
> It turned out that I didn't need drivers, after all, just had to change the permissions on /dev/ttyUSB0

Nice!

Hi DrRus,

General rule of thumb is pretty much any USB to RS232 Serial adaptor with an FTDI chip will work. I use some cheap-o generic brand when I have to interface with old Cisco gear... I also generally have to setup some udev permissions on /dev/ttyUSB0 devices so I don't have to run minicom as root:

```
[ROOT@exodus]# cat /etc/udev/rules.d/50-ttyusb.rules 
# serial
# this is the general rule that covers ttyUSB0 among others
KERNEL=="tty[A-Z]*[0-9]|pppox[0-9]*|ircomm[0-9]*|noz[0-9]*|rfcomm[0-9]*", GROUP="dialout"

# relax the permissions just for ttyUSB0
KERNEL=="ttyUSB0",              MODE="0666"
```

---

### Post by DrRus on 2016-09-11
Thanks for the info King, good to know anything would pretty much work!

---

