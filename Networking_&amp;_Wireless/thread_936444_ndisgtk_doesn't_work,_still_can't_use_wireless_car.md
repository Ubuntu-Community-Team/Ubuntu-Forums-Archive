---
title: "ndisgtk doesn't work, still can't use wireless card"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by wallace412 on 2008-10-02
Here is what happens when I run lshw -C network


[sudo] password for wallace: 
  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 13
       serial: 00:1d:ba:1f:fc:f3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=192.168.1.107 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:bf:00:26:a2:ee
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I tried using Windows XP and Vista drivers in the wrapper, and it says that the hardware is present(still doesnt work) but I don't know much about ubuntu, so I'm stuck

---

### Post by nixscripter on 2008-10-03
It looks like the card is being taken by another driver instead of ndiswrapper.

Install the XP driver into ndiswrapper (Vista drivers don't work), and try this:
```
sudo modprobe -r sky2
sudo modprobe ndiswrapper
```

If it doesn't work, just reboot.

---

### Post by Ayuthia on 2008-10-03
> **nixscripter said:**
> It looks like the card is being taken by another driver instead of ndiswrapper.

Install the XP driver into ndiswrapper (Vista drivers don't work), and try this:
```
sudo modprobe -r sky2
sudo modprobe ndiswrapper
```

If it doesn't work, just reboot.
Actually, the sky2 driver is being used by the wired card so this will disable the wired card.

wallace412, can you post the results of lspci -nn?  Maybe that might help someone figure out what driver you might need.

---

### Post by wallace412 on 2008-10-05
wallace@wallace-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Cantiga Memory Controller Hub [8086:2a40] (rev 07)
00:01.0 PCI bridge [0604]: Intel Corporation Cantiga PCI Express Graphics Port [8086:2a41] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series [1002:95c4]
01:00.1 Audio device [0403]: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series] [1002:aa28]
06:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4232]
08:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 13)
0a:03.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
0a:03.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
0a:03.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
  


and thanks for the help

---

### Post by nixscripter on 2008-10-05
Whoops, you're right Ayuthia. I misread the output.

I was simply trying to make sure that ndiswrapper is loaded for the card. You should still try ```
sudo modprobe ndiswrapper
``` if it says "device installed".

---

### Post by caljohnsmith on 2008-10-05
Wallace412, from both your lshw and lspci output, it doesn't look like you even have a wireless card; you only have an ethernet one. Are you sure you have a wireless card in your computer? If so it's not being recognized that I can see. Maybe you have a USB wireless device? If so post the output of:
```
lsusb
```

---

### Post by wallace412 on 2008-11-15
I do have a wireless card, its on my laptop, I know for a fact it has one. I'm dual booting vista and ubuntu, so on the vista side it works obviously. And its a new laptop so its integrated not usb or something you plug in the side. ( sorry I took so long to respond, been very busy with school and stuff)


here is lsusb:

wallace@wallace-laptop:~$ lsusb
Bus 008 Device 003: ID 054c:0377 Sony Corp. 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 002: ID 05ca:183d Ricoh Co., Ltd 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 003: ID 044e:3017 Alps Electric Co., Ltd 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


i guess its just not recognizing the hardware for some reason, but it does say that it recognizes it in ndisgtk, also I should mention that it is a wireless card with build in bluetooth, here is the model: Wireless LAN: Intel® WiFi Link 5100AGN
(802.11a/b/g/n)

---

### Post by wallace412 on 2008-11-20
any help suggestions?

---

### Post by Ayuthia on 2008-11-20
Based on this:
> 06:00.0 Network controller [0280]: Intel Corporation Unknown device [8086:4232]
and this:
> **wallace412 said:**
> 
i guess its just not recognizing the hardware for some reason, but it does say that it recognizes it in ndisgtk, also I should mention that it is a wireless card with build in bluetooth, here is the model: Wireless LAN: Intel® WiFi Link 5100AGN
(802.11a/b/g/n)

It looks like you should using the iwlagn if you are using Intrepid.  This driver is not in the earlier versions of Ubuntu (the driver was added to the kernel in 2.6.26).  If you are using Intrepid, you can try the following:
```
sudo modprobe -r ndiswrapper iwlagn
sudo modprobe iwlagn
sudo /etc/init.d/networking restart
```

---

### Post by wallace412 on 2008-11-26
i'm new to ubuntu, so what is intrepid

---

### Post by Ayuthia on 2008-11-26
> **wallace412 said:**
> i'm new to ubuntu, so what is intrepid

Sorry, Intrepid Ibex is the code name for Ubuntu 8.10.  You can see what version you have by going into the Terminal and typing:
```
cat /etc/lsb-release
```
It should return something like:
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu jaunty (development branch)"
```
The information will be a little different because I am using a different version.

---

