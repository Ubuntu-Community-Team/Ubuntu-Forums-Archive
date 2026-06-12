---
title: "Wireless Connection Disappears after restart"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by sqrlking on 2007-12-10
Hi,

I've had this problem twice now.  I install 7.1, and right away Ubuntu sees my airlink 101 atheros card, i enable the restricted driver, and everything is fine.  But as soon as I restart, there is no more wireless connection available.   The driver is still there, and active, but there is no wireless connection available in network settings.
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

Help is greatly appreciated, this is driving me crazy.

Thanks

---

### Post by sqrlking on 2007-12-11
Does anyone have any idea what could cause this?  I restarted again, and now the driver has now disappeared as well, and I can no longer see the wireless card in lspci

---

### Post by kevdog on 2007-12-11
Can you post lshw -C network along with lspci -nn

---

### Post by sqrlking on 2007-12-11
```
lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:a5:e4:84:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.101 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=255 mingnt=255

```

```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801BA/BAM AC'97 Audio Controller [8086:2445] (rev 12)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev b2)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller [8086:2449] (rev 03)
02:0b.0 Ethernet controller [0200]: Atheros Communications, Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor [168c:0013] (rev 01)
02:0d.0 Serial controller [0700]: Rockwell International HCF 56k Data/Fax Modem [127a:1003] (rev 01)

```

---

### Post by kevdog on 2007-12-11
Here is your wireless device:

  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=255 mingnt=255

You said that it was supported under the linux restricted wireless drivers (which are really the madwifi drivers).  I know that you stated you loaded or installed the restricted package.  If this is really what you did, what happens when you simply type:

sudo modprobe ath_pci

Then repost
lshw -C network

---

### Post by sqrlking on 2007-12-11
I did modprobe, and it asked for a password.  I can see the restricted driver again, but still no wireless connection option in the network.

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:a5:e4:84:e8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI firmware=N/A ip=192.168.1.101 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications, Inc.
       physical id: b
       bus info: pci@0000:02:0b.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=255 mingnt=255

```

---

### Post by sqrlking on 2007-12-11
Now the card doesn't show up again, and the driver isn't in the restricted driver s list.

```
 lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801BA/BAM/CA/CAM Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:02:a5:e4:84:e8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=full firmware=N/A ip=192.168.1.101 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

```

What can I do to make this card show up?

---

### Post by kevdog on 2007-12-11
Your card according to the madwifi website should be supported with the madwifi drivers, but for some reason its not working.  I would try one of two solutions at this point

Uninstall the linux restricted drivers for the wireless card and

#1 - Download, compile and install the madwifi drivers 
#2 - Ndiswrapper

---

### Post by sqrlking on 2007-12-12
Could this be a hardware issue or something?  It confuses me that the card & driver worked perfectly until I restarted.  

I'll try uninstalling tonight & using ndiswrapper

---

### Post by sqrlking on 2008-05-06
I know this is an old, old post.  

I ended up reinstalling 2 or 3 times, and after the last install, it worked.  I think it may have been a problem with the install disk itself, because I had other trouble, but after i downloaded a new .iso, everything installed fine.

---

