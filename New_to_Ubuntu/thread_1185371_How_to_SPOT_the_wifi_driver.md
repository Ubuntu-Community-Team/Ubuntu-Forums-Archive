---
title: "How to SPOT the wifi driver??"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by exus69 on 2009-06-12
Am using Ubuntu 9.04. It has the generic drivers for my Edimax EW-7318USg USB Wifi adapter. I know it uses the driver starting with something like rt.... so I ran lsmod to check it. However I was surprised to find many modules starting with rt.... for eg. rt73usb, rt2500usb, rt2x00usb etc. etc.

So heres my query, which of the above mentioned modules is used by my wifi adapter?? Are all of the modules starting with rt used by my wifi adapter? I've read somewhere that rt73 is a different driver than rt2500.

Please help

Sunny

---

### Post by Johan-Steyn on 2009-06-12
Hi exus69,

Open the terminal and type "**lspci**" and enter your password when prompted.

This will display a list of all installed hardware.

Mine is as follows:
[php]06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
[/php]Hope it helps.

What output does the following code give?
[php]lsmod | grep rt73[/php]

Regards, 

JS

---

### Post by glennric on 2009-06-12
> **Johan-Steyn said:**
> Open the terminal and type "**lspci**" and enter your password when prompted.

This will display a list of all installed hardware.


Actually lspci only displays hardware on the PCI bus.  Since his network adapter is USB he should use lsusb.  Also, this won't help him since he already knows what kind of network adapter he has.  His question is about the kernel module (or driver) for the adapter.

---

### Post by exus69 on 2009-06-12
Hello JS,

lspci dint help me but I got the following output when I typed lsusb :

[PHP] Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter[/PHP]

But which driver is it using according to lsmod coz its showing different modules starting with rt...

Sunny

---

### Post by glennric on 2009-06-12
If you want to find more information about the modules available on your system type "modinfo module_name".  For example to find out about the rt73usb module type "modinfo rt73usb".

---

### Post by Sealbhach on 2009-06-12
If you run 

```
lshw -C network
```it will tell you what driver is being used by each interface.

.

---

### Post by glennric on 2009-06-12
Also, if you are using Network Manager and are connected to a network via that adapter, then you can right click on the nm-applet in the system tray and select "Connection Information" from the drop down menu.  That will open a window that (among other things) tells you which driver is being used.

---

### Post by exus69 on 2009-06-12
I just found out through googling that my usb adapter uses the rt73 drivers so maybe the other generic drivers for eg. rt2500 are part of the rt family used for other kind of network interfaces like pcmcia. Please correct me if I am wrong after 'maybe'

A BIG THANK YOU to all of you for helping:))

Sunny

---

