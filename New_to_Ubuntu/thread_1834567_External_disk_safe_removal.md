---
title: "External disk safe removal"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by vagelism on 2011-08-27
Hello to all!
Well this is pretty strange problem. When I attach a usb pen drive to my pc everything works great from start till to un mount it!
When I attache the external usb hard drive still works great but when I choose to safe remove it , after some seconds if I dont pull the plug out of the usb, then the system remounts it and is there ready and working!
Any ideas?
Thank you!

---

### Post by coffeecat on 2011-08-27
> **vagelism said:**
> Any ideas?

Do you have a USB controller with a nvidia chipset? If you are not sure, the output of "lspci" in the terminal will tell you. If you do, you have been hit with this bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755)

Duplicate here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085)

---

### Post by vagelism on 2011-08-27
> **coffeecat said:**
> Do you have a USB controller with a nvidia chipset? If you are not sure, the output of "lspci" in the terminal will tell you. If you do, you have been hit with this bug:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/624755)

Duplicate here:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/792085)

Seems not...!!!! Here is the output:
```
unknown@unknown-DURABOOK:~$ sudo lspci
[sudo] password for unknown: 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

What do you think?
Thank you!

---

### Post by coffeecat on 2011-08-27
The reason I wondered about a nvidia chipset is because several people who contributed to the first bug have one. In my collection of machines, those with Intel or AMD USB controllers are not affected by this issue, but the one with nvidia is.

Apart from safely removing a second time, I can't suggest anything else. Sorry.

---

### Post by AlphaLexman on 2011-08-27
I also have an Nvidia card, and if I click on 'Safely Remove Drive" and I don't actually unplug it in a certain amount of time, it automatically re-mounts after some time period without my permission. Usually, I just make sure I un-plug the USB-cord before it re-mounts.

---

