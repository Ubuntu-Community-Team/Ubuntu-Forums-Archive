---
title: "Wireless dongle worked, then it didn't (possibly because of ndiswrapper)"
date: 2014-07-02
forum: Networking &amp; Wireless
---

### Post by danielgrosvenor on 2014-07-02
Hi guys. I have attempted to search for this issue on the forum but am admittedly quite unfamiliar with Linux (particularly Terminal and installing drivers) so I apologise in advance if this issue has been resolved previously.

I've installed Ubuntu 14.04 LTS (64-bit) on an ageing Dell Optiplex 760, and plugged in a TP-Link wireless USB adapter (model TL-WN722NC). WiFi seemed to connect as soon as I plugged it in and everything was great, but it was reporting a very weak signal (despite the machine being literally 2 inches from the router as I'd have it connected via ethernet during the install). Thinking it might need a driver update I installed ndiswrapper, inserted the driver CD and selected the Windows 7 x64 driver.

When I next rebooted the machine I got a bunch of ndiswrapper-related error messages on a black screen before the Ubuntu splash screen, and when I logged in the wireless connection had disappeared completely.

I tried removing both the driver from within ndiswrapper and even removing ndiswrapper itself via Software Centre, and while that got rid of the error messages upon bootup I still can't connect wirelessly. I've tried plugging the dongle into different USB ports and running **sudo service network-manager restart** in Terminal, but still no luck.

*Tl;dr --> Wireless dongle worked by simply plugging it in, but once I touched ndiswrapper the computer no longer connects to WiFi.*

I ran the wireless script and have pasted the output below. Most of it makes no sense to me but **ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel** did stand out.

```



########## wireless info START ##########


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux MattyComputer 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection [8086:10de] (rev 02)
    Subsystem: Dell Device [1028:027f]
    Kernel driver in use: e1000e


##### lsusb #####


Bus 002 Device 002: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 008 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### lsmod #####


ndiswrapper           283985  0 


##### iw reg get #####


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


##### iwlist channel #####


##### modinfo #####


filename:       /lib/modules/3.13.0-30-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.0-30-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### modules #####


lp
rtc


##### blacklist #####


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x8086:0x10de (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   12.582189] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   12.582949] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)


########## wireless info END ############

```


Any help would be greatly appreciated.

---

