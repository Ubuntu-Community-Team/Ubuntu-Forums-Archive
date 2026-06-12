---
title: "Lost all networking after upgrade."
date: 2008-09-14
forum: Networking &amp; Wireless
---

### Post by RavUn on 2008-09-14
I was able to solve the issue by following:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

I have the Dell WLAN 1395 card and it originally showed as BCM4310 USB Controller in lspci initially.  After installing updates it changed to BCM4312 in lspci and I could not connect to WPA networks.  Once I did what was posted in [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) it works fine.

The threads below this are just me asking questions, but don't have much info in them.

--------------------------------------------------------------------

I bought a Dell laptop today and spent some time setting it up for wireless.  After I finally get it working with ndiswrapper I installed the 142 updates that I kept getting pop-ups about.  Now, after rebooting, I can no longer connect wirelessly.  I can click on the network icon in the status bar and it shows wireless, but no networks showed.  I opened up the network configuration in System -> Administration -> Network and was trying to enter a manual configuration but that didn't work either.  I've checked the hardware drivers and my driver is enabled and in use.

EDIT: I originally had it as "lost all networking" because I couldn't connect wired either, but that was a small mistake in the network settings I made.

EDIT2:  I rebooted again and the wireless network showed back up but now it does not connect.  I've tried several times and even tried someone else's wireless that's open access.  I booted up to Vista and can connect to both just fine.

---

### Post by RavUn on 2008-09-15
I tried using WICD and had the same issue.  I've reinstalled network manager and now it connects to someone's wireless that's open access but it will not connect to my network that has WPA.  It worked fine before... I deleted the settings for that connection and retyped the key and it still does not work.  I've been connecting to the open access wireless just fine, though.

After typing in passkey it'll say "Waiting for network key for the wireless network 'yellow jackets'..."

Here's iwconfig (I'm currently connected to a wireless access point called "linksys"):
```

kyle@kyle-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated  
```

here's lspci
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

Here's lshw -C network:
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:c6:d3:09
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.1.106 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:da:b3:5e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 latency=0 module=tg3 multicast=yes

```

I don't know what else is needed.

---

### Post by RavUn on 2008-09-16
One thing I don't understand is that when I do lspci it shows: 
```
Broadcom Corporation BCM4312 802.11b/g (rev 01)
```
but, when I ran lspci before it showed:
```
Broadcom Corporation BCM4310 USB Controller (rev 01)
```

I put in the livecd and checked and it shows BCM4310 USB Controller when I do... I followed these instructions to get it working initially [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) then installed a bunch of updates and it stopped working right after rebooting.  I don't know if it was the update that screwed things up or if it was coincidental.  i'm thinking of reinstalling ubuntu and trying to follow this guide: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218) but I don't know for sure if I am using a BCM4310 USB controller or the BCM4312.  

I'm confused... any ideas before trying a reinstall?  I don't have anything to lose so reinstalling doesn't seem too bad for me.  I've been able to connect to the same open access point but not my WPA access point.  I don't know if it's an issue with wpa_supplicant but I've been unable to figure out what it could be.

---

### Post by RavUn on 2008-09-16
I don't understand what's going on or if this is how it's supposed to work...
I reinstalled Ubuntu and checked lspci and it showed:
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

then I didn't do anything except install the 120 updates that showed in update manager and it changed to:
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Is that how it's supposed to work?  Do I use NDISWrapper for BCM4310 or 4312?

Does anyone have input on any of this????  I wish I knew which update was causing that problem.  I'm going to try doing this:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

EDIT (I'm having a nice conversation with myself):
Hmm, so I guess that update was supposed to happen because without changing anything my wireless card is already enabled and in use and I see all of my wireless networks.  However, the problem I was having before is that it does not connect to WPA.  I can connect to an open network, but not my own WPA network.

When I did it all before I had it working with WPA when it showed as BCM4310 USB Controller (before the updates) and everything was perfect.  Then, i installed the updates and it changed to BCM4312 and I was where I am now.  I don't understand why WPA is not working but it's very agitating.  I wish I knew how to reverse whatever was updated or at least get WPA working....??

---

