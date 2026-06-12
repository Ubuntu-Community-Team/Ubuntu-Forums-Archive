---
title: "Having Prob in Switching in Wireless..."
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Helix_Spear on 2007-04-30
Hi all,
i am new to linux enviroment... i ahve no idea on how get my wireless switched on and get it connected to my router... can somebody help me... i am using Lenovo R60...

---

### Post by Floppyjoe on 2007-04-30
You need to find your wireless cards chipset first:
Open a terminal by clicking on Applications/Accessories/Terminal.
Then:either:
```
lsusb
```
for a Usb wireless device or:
```
lspci
```
for a pci based wireless device.

Then you can proceed from there. Post the outputs here please.

---

### Post by Helix_Spear on 2007-04-30
helix@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 21)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
helix@ubuntu:~$

---

### Post by Floppyjoe on 2007-04-30
> Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
This is your wireless network interface.
Now you need to search the forums to find a guide that will enable you to get that device working if it does not already work. So I would do a search for "IPW 3945ABG" to see if that turns up anything.

---

### Post by Helix_Spear on 2007-04-30
Do i need to install any centralised wireless manager packages to control my wireless...

---

### Post by Floppyjoe on 2007-05-01
If you have a desktop computer that you will not be roaming around with then you don't need a connection manager (you could just edit your configuration files) but if you are using a laptop i would probably use network-manager to enable roaming. WICD is another manger that a lot of people are talking about. I have no experience with wicd.

---

### Post by Helix_Spear on 2007-05-03
Thanks Joe i need to look in to my router setting on the mac filter...
I have already allow my notebook to connect to my router in windows...
Do i have to reconfig my router for ubuntu...

---

