---
title: "Lenovo ThinkPad T61 with Sierra Wireless HSPDA MC8755"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by DebianLover on 2008-05-14
Okay, here is the problem: I have read many quides but not succeeded to make connection. Ubuntu 8.04 default installation (i386) install driver and I can detect that I have integrated Sierra HSPDA card on board:

```

pex@toosa:~$ **dmesg | grep sierra**
[   25.815845] sierra 6-1:1.0: Sierra USB modem (3 port) converter detected
[   25.818092] usbcore: registered new interface driver sierra
[   25.818094] /build/buildd/linux-2.6.24/drivers/usb/serial/sierra.c: USB Driver for Sierra Wireless USB modems: v.1.2.5b

pex@toosa:~$ **lsusb**
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 1199:6813 Sierra Wireless, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000


```

But when I try to communicate with the modem and get any kind of info from that card:

```

pex@toosa:~$ **gcom -d /dev/ttyUSB2**
gcom 16:26:42 -> -- Error Report --
gcom 16:26:42 -> ---->                       ^
gcom 16:26:42 -> Error @74, line 4, Could not write to COM device. (1)

```

I have tried USB0, USB1 etc... any ideas?

***** EDIT *****

Now suddenly after many reboot **gcom -d /dev/ttyUSB2** is asking a PIN-code so it works!

```

pex@toosa:~$ **gcom -d /dev/ttyUSB2** 

Enter PIN number: 

```

but even if I give the right PIN it says that it is wrong.. In phone i verified that PIN works and it's not locked out.. IDEAS?

---

