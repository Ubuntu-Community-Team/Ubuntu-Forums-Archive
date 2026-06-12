---
title: "Broadcom BCM4360 802.11ac doesn't see wifi networks"
date: 2015-08-24
forum: Networking &amp; Wireless
---

### Post by jrussell88 on 2015-08-24
I'm running a fresh install of Ubuntu 15.04 x64 (but had the same issue with 14.10) on a MacBook Retina Pro 12,2, and used Additional Drivers to install the Broadcom driver from bcmwl-kernel-sources. 

Most wireless networks aren't visible on Ubuntu. To use open wifi networks I usually have to tether an Android device with a USB cable as they are visible from any Android device. It doesn't appear to be related to security ie WPA or WPA2. Signal strength doesn't appear to be relevant either as an Android wifi hotspot next to my laptop remains invisible.

I haven't found the same problem anywhere else - can anyone suggest what the cause or cure might be?

Some info about my setup: 
```
john@john-MacBookPro-Ubuntu-15:~$ lspci -nn | grep 028002:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
```

```
john@john-MacBookPro-Ubuntu-15:~$ lspci -vvnn | grep -A 9 Network 02:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
	Subsystem: Apple Inc. Device [106b:0134]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 256 bytes
	Interrupt: pin A routed to IRQ 18
	Region 0: Memory at a0600000 (64-bit, non-prefetchable) [size=32K]
	Region 2: Memory at a0400000 (64-bit, non-prefetchable) [size=2M]
	Capabilities: <access denied>
	Kernel driver in use: wl

```

```
john@john-MacBookPro-Ubuntu-15:~$ rfkill list0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```

john@john-MacBookPro-Ubuntu-15:~$ sudo lshw -C Network
[sudo] password for john: 
  *-network               
       description: Wireless interface
       product: BCM4360 802.11ac Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan1
       version: 03
       serial: b8:e8:56:3a:42:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.248 (r487574) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:18 memory:a0600000-a0607fff memory:a0400000-a05fffff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:57:0f:09:31:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.202 link=yes multicast=yes
```

```
john@john-MacBookPro-Ubuntu-15:~$ iwconfig
usb0      no wireless extensions.


lo        no wireless extensions.


wlan1     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by Vladlenin5000 on 2015-08-24
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

