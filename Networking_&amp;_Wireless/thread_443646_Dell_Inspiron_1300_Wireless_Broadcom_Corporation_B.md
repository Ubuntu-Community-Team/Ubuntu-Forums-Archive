---
title: "Dell Inspiron 1300 Wireless Broadcom Corporation BCM4311 Wont Work"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by earobinson on 2007-05-14
I have a Dell Inspiron 1300 and try as I might I still cant get the wireless to work

```
earobinson@NaN:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)

```

Has anyone had any luck with this laptop? Any help would be great. Thanks in advance guys.

Everything else works perfect.

---

### Post by josephus on 2007-05-14
what have you tried so far?  there are a number of posts on getting broadcom cards to work in ubuntu, but basically you either need to use ndiswrapper or bcm fwcutter.

---

### Post by earobinson on 2007-05-14
I have tried may ndiswraper soultons none have worked, examples are:
the ubuntu wiki soultion
a couple of posts on the fourms eg [http://ubuntuforums.org/showthread.php?t=346083](http://ubuntuforums.org/showthread.php?t=346083)
some french website.

Im intrested in this fwcutter soultion

---

### Post by earobinson on 2007-05-14
Ok, I feel a bit dumb now (due to the amout of time I avoided trying this soultion) [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) solved it for me, the weird thing is I only had to do steps 1 2 and 3 and that was it.

Any ideas why.

Thanks a lot for the hint.

---

### Post by josephus on 2007-05-14
glad it works. 

but getting it to work by doing only steps 1-3 makes no sense at all.  better not think about it too much and just be glad that it works.

---

### Post by earobinson on 2007-05-14
But knowing why things work lets you help others. But yes Im glad it works

Thanks

---

### Post by josephus on 2007-05-14
ok. can you post 
```

lshw -C network
```

i just want to see which driver is being used.

edit: did it automatically ask you to fetch and extract the firmware when you installed the fwcutter, because that's what it did for me running feisty?  if that is the case then the important fourth step is unnecessary.  the remaining steps after that aren't really important.

---

### Post by earobinson on 2007-05-14
earobinson@NaN:~/Desktop$ lshw  -C network
WARNING: you should run this program as super-user.
  *-network:0            
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:99:5c:91
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=64 multicast=yes
       resources: iomemory:dfbfc000-dfbfdfff irq:19
  *-network:1
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:4a:d0:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic ip=192.168.1.100 latency=64 multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfbfe000-dfbfffff irq:18

earobinson@NaN:~/Desktop$ sudo lshw  -C network
Password:
  *-network:0            
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:99:5c:91
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:dfbfc000-dfbfdfff irq:19
  *-network:1
       description: Wireless interface
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:4a:d0:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic ip=192.168.1.100 latency=64 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfbfe000-dfbfffff irq:18

---

### Post by earobinson on 2007-05-14
I cant really remember what happened during the install, a bunch of text went by, I turned my back to check on something else and when I looked back It had connected to my neighbors network.

---

### Post by yebouadominic on 2007-12-05
i have lost my ethernet controller, network controller, pci device video controller, video controller(VGA compatible) for my laptop dell inspiron 1300 after a fresh re-installation.  i am looking for all these drivers.

---

