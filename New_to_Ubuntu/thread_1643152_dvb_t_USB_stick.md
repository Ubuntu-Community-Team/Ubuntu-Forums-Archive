---
title: "dvb t USB stick"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by albert s on 2010-12-11
hi, I have inherited a USB dvb dongle,
but I have absolutely no idea what to do with it,
I installed mythtv but still have no idea what I am doing.
I have done some searching and got this

[http://cateee.net/lkddb/web-lkddb/DVB_USB_AF9015.html](http://cateee.net/lkddb/web-lkddb/DVB_USB_AF9015.html)

and the results of lsusb

```

```marko@marko-desktop:~$ lsusb
Bus 005 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0458:0007 KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```

---

### Post by albert s on 2010-12-11
according to this it is supported,

[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Supported_DVB-T_USB_Devices_.28old_data.29](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Supported_DVB-T_USB_Devices_.28old_data.29)

but I have no idea how to get it working,
Im just a plug and play kinda person, getting a search engine to work is hard for me.  :o

---

### Post by albert s on 2010-12-12
bump,
anyone.?

---

### Post by TopEnder on 2010-12-15
Albert s,  What happen when you plug the stick in to the USB port and do a seach for Hardware Drivers via: System/Administration/Hardware Drivers.   I found that all I had to do for the USB stick, then in stall your viewing program, I use VLC & metv, the latter allows you to scan for TV channels with in the program., and not as complicated as Myth-TV.  TopEnder

---

