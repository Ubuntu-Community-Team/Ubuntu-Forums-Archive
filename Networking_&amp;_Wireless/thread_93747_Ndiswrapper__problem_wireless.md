---
title: "Ndiswrapper : problem wireless"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by TiteFleur on 2005-11-22
Hello,
At first, sorry for my english, I'm french ;)
But I need some help about my wireless card.
It's a Broadcom chipset, and I know I need Ndiswrapper to install it.
So I've done that, Ndiswrapper is installed and Ubuntu says the driver is well installed, the hardware is present.
But (because there is a "but"), when I tape "dmesg" in a terminal, it send me :

> [  726.143067] ndiswrapper version 1.5 loaded (preempt=no,smp=no)
[  726.154706] ndiswrapper: driver bcmwl5a (Broadcom,07/17/2003, 3.30.15.0) loaded
[  726.159920] ndiswrapper (NdisWriteErrorLogEntry:219): log: C000138D, count: 1, return_address: d8b84be3
[  726.159931] ndiswrapper (NdisWriteErrorLogEntry:222): code: 259
[  726.160038] ndiswrapper (miniport_init:767): couldn't initialize device: C0000001
[  726.160046] ndiswrapper (ndiswrapper_start_device:1441): Windows driver couldn't initialize the device (C0000001)
[  726.160054] ndiswrapper (ndiswrapper_add_pci_device:200): couldn't start device
[  726.160072] ndiswrapper: probe of 0000:03:02.0 failed with error -22


It's not very good...
Moreover, if I tape "iwlist wlan0 scanning", it send me :
> wlan0     Interface doesn't support scanning.

I don't know what I must do !
Can you help me please, I want delete Windows !! :p It's the last thing.

Thank you for advance,
Marion.

---

### Post by Lambert on 2005-11-22
What driver did you use? If you used the one off the disk that came with the device, it's possible it won't work.

Click on the wireless troubleshooting guide below and find the section on common ndiswrapper problems. This will point you how to find the correct driver and where to get it from. Then start over again installing this new driver.

You will need to remove the current installed driver using these steps.

```
sudo modprobe -r ndiswrapper
``` 
then

```
sudo ndiswrapper -e [current_installed_driver]
```

---

### Post by taurus on 2005-11-22
What is the brand name and model of your wireless lan card anyway?  Any chance you have a Linksys WPC54G!!!

---

### Post by TiteFleur on 2005-11-23
I don't use the driver on the disk but one I've found on the Internet, but I don't remember where exactly.
Some people on a forum about the Compaq R4000 (my laptop) have installed it and a few have success.
It's the bcmwl5a driver, and I've installed bcmwl5 too, I don't know if it's necessary...
I'm going to read your links, and I'll try something this evening.
It's boring to have to go on Windows for the Internet each time !
Thanks

---

### Post by TiteFleur on 2005-11-23
It works !!!!
I've tried to remove the driver, and to install the Windows driver (of the disk), and that works !!
All is known by linux.
But before to say if the connexion works, I must ask the key wep at the person who has the network.
Thanks a lot !!

---

### Post by wubrgamer on 2006-04-30
if you could tell me what you did to fix it i'd appreciate greatly

---

