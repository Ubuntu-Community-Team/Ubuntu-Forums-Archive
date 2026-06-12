---
title: "No Internet Connection after installation"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by dunnthetown on 2007-09-11
I will try to make this as clear to understand as possible. I have a Dell 2200 laptop. The first time I ever installed Ubuntu 7.04: it detected a network connection. I decide to buy the CD because I got a Gnome error after installing Ubuntu from a iso that I found from Bit Torrent. I pop the CD in and install it and it brings me to the live setup. Before I was able to connect to the internet from the live portion (the part where you decide to install Ubuntu when you have Windows already) I install full disk installation (before then: I did not detect a network) It restarts then I find no network connection even after the live portion. So I do my research to see how I can do get this to work and it says that I need to install ndiswrapper. I tried installing the packages from the package manager and nothing happened. Then I read that I need to use the drivers for network card, but that isn't going to work because they are from Dell. They obviously use different file associations. How can I install ndiswrapper?

---

### Post by noob12 on 2007-09-12
Can you plug in wired and post some information from running these commands on your box?
```

lspci -nn

sudo lshw -C network

```

---

### Post by jualin on 2007-09-12
I am new with Ubuntu but I think that ndiswrapper lets you load the windows drivers. The only bad thing is that you need to have the drivers from windows. Anyways what is the model and brand for the network card?

---

### Post by jualin on 2007-09-12
I forgot to tell you how to install it, lol.
Open Adept Manager and search for the package ndiswrapper-common. Another way is opening the Konsole and typing 
sudo apt-get install ndiswrapper-common.
I hope this helps.:)

---

### Post by dunnthetown on 2007-09-12
> **noob12 said:**
> Can you plug in wired and post some information from running these commands on your box?
```

lspci -nn

sudo lshw -C network

```
```

00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile [8086:1068] (rev 03)
 *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 02
       serial: 00:90:4b:de:46:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfdfe000-dfdfffff irq:19
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:04:c2:09
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:dfdfd000-dfdfdfff ioport:df40-df7f irq:20
```

---

### Post by dunnthetown on 2007-09-12
> **jualin said:**
> I forgot to tell you how to install it, lol.
Open Adept Manager and search for the package ndiswrapper-common. Another way is opening the Konsole and typing 
sudo apt-get install ndiswrapper-common.
I hope this helps.:)

I tried that this what came up.

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (var/lib/dpkg/), are you root?

---

### Post by noob12 on 2007-09-12
dunnthetown:  I would recommend you try following the HOWTO in this thread:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by dunnthetown on 2007-09-12
> **noob12 said:**
> dunnthetown:  I would recommend you try following the HOWTO in this thread:
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I tried it. I got a few errors while installing it. Cannot find such directory. I restarted the computer and nothing took effect.

---

### Post by noob12 on 2007-09-12
You might want to try posting on that thread for help.  The authors are generally monitoring it and you'll get good help. You should indicate where you are getting the error and what the actual error message says.

---

