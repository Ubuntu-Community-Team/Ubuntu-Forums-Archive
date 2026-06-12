---
title: "Acer v3-572G &amp; BCM43228 cause System crash &amp; Freeze on Ubuntu 14.04/15.04"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by gmatti.93 on 2015-09-30
Hi guys i have the big problem , i hope to resolve with you .
I have tried to install Ubuntu 15.04 and 14.04 now i have installed 14.04.
My problem is the driver for BCM43228
When i run this command from shell

```
$ sudo apt-get update$ sudo apt-get install linux-headers-generic
$ sudo apt-get install bcmwl-kernel-source
```

the wifi interface is recognized , but after a few minutes my system crash and freeze 
Keyboard not working (ctrl+alt+F1) mouse not working my only chance is Force reboot by power button.
 I also installed the nVidia drievr , but still not working , when i connect to a wifi connection the system crash all!!
My chance to use internet connnection is plug in a usb wifi card , it is recognized correctly and work perfectly.

What is the problem ?

PS: Sorry for my bad english , i hope you understand !

Thanks in advance
Best regards 
Mattia

---

### Post by gmatti.93 on 2015-09-30
The problem it seems solved 
i've installed 
[apt://firmware-b43-installer](apt://firmware-b43-installer)

---

### Post by gmatti.93 on 2015-10-01
Guys i have another problem , when i use a wifi connection , sometimes I lose connection . I have tested two wifi connection the problem still present.

---

### Post by gmatti.93 on 2015-10-03
[COLOR=#000000]Another update when I connect to the network using a static ip, my Ubuntu crashes. The only way out is a hard reset. Please help.[/COLOR]

---

### Post by jaseem2 on 2015-10-30
Guys I have the same problem with my Dell Laptop with Broadcom 802.11n network adapter. Both Ubuntu 15.04 and 14.04 LTS is crashing/freezing with Stattic ip. Please help..

---

