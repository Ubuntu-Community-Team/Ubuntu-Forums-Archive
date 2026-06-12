---
title: "Better wireless connection in Ubuntu?"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by khr on 2008-06-25
The router is in the first floor and I'm trying to connect to it from the second floor. I've tried connecting to the router several times but I can't do it from the second floor. I tried to connect to it with Windows and it works at near full speed. Is there anything I can do to make it possible to connect to the router from second floor?

---

### Post by chalewa on 2008-06-25
im assuming it connects on the first floor right?

---

### Post by earthmeLon on 2008-06-25
Are you sure your wireless card is installed correctly?  If you can see other routers, then it probably is. 

try running the command iwconfig and see what that returns

---

### Post by plewisfdx on 2008-06-25
paste the output of

1. lspci
2. iwconfig (while standing right next to the router)
and
3. iwconfig (in the room desired)

---

### Post by khr on 2008-06-25
I _can_ connect to the router, but not from the second floor.
I can only connect from the second floor with windows, but not with Ubuntu!
**I'm actually asking how I can "improve" the "wireless connecting" Ubuntu so i can connect to the router from the second floor with Ubuntu.**

---

### Post by plewisfdx on 2008-06-25
Sorry, I guess you can't do that then, hmmm.  

lspci output?

---

### Post by khr on 2008-06-25
> **plewisfdx said:**
> Sorry, I guess you can't do that then, hmmm.  

lspci output?

lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
```

---

### Post by plewisfdx on 2008-06-25
ok the intel 3945 should work just fine.

From your original post its a little confusing, have you configured the card and are able to connect to ANY wifi networks in ubuntu?

Are you using hardy and wireless manager?  

If you cannot connect from the same room, then I would assume you don't have it configured properly.

Paste the output of iwconfig if you think you do have it configured properly.

---

### Post by khr on 2008-06-25
> **plewisfdx said:**
> ok the intel 3945 should work just fine.

From your original post its a little confusing, have you configured the card and are able to connect to ANY wifi networks in ubuntu?

Are you using hardy and wireless manager?  

If you cannot connect from the same room, then I would assume you don't have it configured properly.

Paste the output of iwconfig if you think you do have it configured properly.

I'm sorry for all the confusion, but Ubuntu can connect to any wifi networks.
Yes, I'm using hardy and wireless manager.

I'll go to sleep now, cya sometime tomorrow.

---

