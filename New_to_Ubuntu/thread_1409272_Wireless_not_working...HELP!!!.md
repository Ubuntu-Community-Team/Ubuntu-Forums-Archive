---
title: "Wireless not working...?HELP!!!"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by ace8187 on 2010-02-17
Hey guys i am a noob to ubuntu...
 
I just installed Ubuntu 9.10 on a Compaq Presario C304NR and the wireless does not work I was wondering if someone could help me with how to go about getting it to work.
 
 
 
Thank You

---

### Post by halitech on 2010-02-17
could you open a terminal and run the following and post the output back here for us
```
lspci
```
```
lsusb
```

reason I'm asking for both is some wireless cards in laptops use the PCI bus and some connect via usb.

---

### Post by ace8187 on 2010-02-17
when i run the 
lspci

I get the addresses of the different devices connected to the laptop. I am unable to get any kind of connection a wired or wireless on the laptop so i am unable to just copy and past what it says but here is the jist of the lspci well its the stuff i think you may be looking for 

"06:00.0 Network controller: Broadcom Corporation BCM4311 802.11B/G wlan (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co. , Ltd. RTL-8139/8139C/8139C+ (REV 10)"

AND

lsusb
it basically lists all the usb hubs...nothing else

hopefully this is enough information

---

### Post by lkraemer on 2010-02-17
Read this and it should help you get the Wifi working.
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

lk

---

### Post by ace8187 on 2010-02-27
thank you it has been resolved

---

