---
title: "[SOLVED] Have a look at this Kevdog..."
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by dwdarkstar on 2008-02-28
[SIZE="3"][FONT="Book Antiqua"]Hey Kevdog (and other roast masters), your HOW TO posts are very helpful, unfortunately I have been unable to resolve my issue after two weeks of trial and error and frustration.  Let me briefly describe my problem before providing terminal outputs below.

I have an Averatec 3200 series laptop on which I ran Dapper as the single OS for two years with no problems, no system crashes, ever.  Two weeks ago I installed Gutsy and lost my Ethernet connection.  I am not concerned with wireless at this time, only a working LAN connection.  I have an Intellinet Broadband Router servicing two XP machines and my laptop.  The router/modem work flawlessly with the XP machines, and previously worked with my laptop.  After the Gutsy install I can not get outside my laptop.  It acknowledges the existing network, even reports a connection, but no data is successfully transmitted or received.

To complicate matters further, my system will crash when trying to configure eth0 using Network Admins OR Terminal.  In the following terminal code I have indicated commands that resulted in a system crash by typing them in red.  A CS professor attempted to diagnose my issue today but was unsuccessful, however he suspected the avah could be causing the problem, but my machine crashed during his inspection.  I am waiting on another CS professor/Networking-genius(former SunMicrosystems programmer, worked on Netbeans R&D, plays golf with Amazon CEO) to return from Europe next week, but would rather not "bother him" if I can help it.  There is a sign on his door that reads "I will Google before asking STUPID questions."    So, please help me with this issue if you can.    Thank you.[/FONT][/SIZE]

```
Z:~$lspci

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 20)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)

```
```
Z:~$sudo lshw -C network

  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@00:09.0
       logical name: eth1
       version: 03
       serial: 00:90:4b:6c:b4:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=32 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:dfffe000-dfffffff irq:11
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:40:45:18:95:8b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.2 duplex=full latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100MB/s
       resources: ioport:d800-d8ff iomemory:dfffde00-dfffdeff irq:11

```
```
Z:~$sudo ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:40:45:18:95:8B  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:26 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1865 (1.8 KiB)  TX bytes:3405 (3.3 KiB)
          Interrupt:11 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:6C:B4:B2  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 

eth0:avah Link encap:Ethernet  HWaddr 00:40:45:18:95:8B  
          inet addr:169.254.6.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9488 (9.2 KiB)  TX bytes:9488 (9.2 KiB)

```
```
Z:~$route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

```
```
Z:~$sudo cat /etc/resolv.conf

search cs.oswego.edu
nameserver 192.168.2.1
```
```
Z:~$sudo iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```
```
Z:~$sudo ifconfig eth0:avahi down

```
```
Z:~$sudo /etc/init.d/avahi-daemon stop

 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                           [ OK ] 

```
```
Z:~$sudo ifconfig eth0 down

```

```
Z:~$sudo dhclient -r eth0

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:40:45:18:95:8b
Sending on   LPF/eth0/00:40:45:18:95:8b
Sending on   Socket/fallback

```
```
Z:~$[COLOR="Red"]sudo ifconfig eth0 192.168.2.101 netmask 255.255.255.0 up


```[/COLOR]
[INDENT][SIZE="3"]ping eth0:avah[/SIZE][/INDENT]
```
Z:~$ping 169.254.6.30

PING 169.254.6.30 (169.254.6.30) 56(84) bytes of data.
64 bytes from 169.254.6.30: icmp_seq=1 ttl=64 time=0.093 ms
64 bytes from 169.254.6.30: icmp_seq=2 ttl=64 time=0.090 ms
64 bytes from 169.254.6.30: icmp_seq=3 ttl=64 time=0.089 ms

--- 169.254.6.30 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.089/0.090/0.093/0.011 ms

```
[INDENT][SIZE="3"]ping lo[/SIZE][/INDENT]
```
Z:~$ping 127.0.0.1

PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.098 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.083 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.081 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.081/0.087/0.098/0.010 ms

```
[INDENT][SIZE="3"]ping my networks actual IP[/SIZE][/INDENT]
```
Z:~$ping 192.168.2.101

PING 192.168.2.101 (192.168.2.101) 56(84) bytes of data.
From 169.254.6.30 icmp_seq=1 Destination Host Unreachable
From 169.254.6.30 icmp_seq=2 Destination Host Unreachable
From 169.254.6.30 icmp_seq=3 Destination Host Unreachable

--- 192.168.2.101 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4016ms
, pipe 3

```
[INDENT][SIZE="3"]ping ubuntu.com[/SIZE][/INDENT]
```
Z:~$ping ubuntu.com

ping: unknown host ubuntu.com

```
[SIZE="3"][FONT="Book Antiqua"]I am working the graveyard shift tonight and will be unable to respond to posts until ~12pm tomorrow(2/29/08).  Thank you for your time and the help you provide, if it was not for Ubuntu Forums and others like it; Linux would continue to be a foreign language for the average user.    [/FONT][/SIZE]

---

### Post by kevdog on 2008-02-28
Being summoned by name for a title of a post??  

And just to clarify, Im not roastmaster -- just an average everyday user just like everyone else in the forums here.  Don't be fooled, I am no linux master.

Anyway a couple of things spring to mind.

1. Do you still have access to the old installation??  Just wondering what driver you were using back then.  Currently you are using:
driver=via-rhine driverversion=1.4.2

2. After booting -- check dmesg before configuring any interface. Is there any error message related to the loading of the via-rhine kernel module.

3.  You have no Universal Gateway configured in your routing table:

Z:~$route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

You would add a universal gateway with the syntax similar to the following:
sudo route add default gw 192.168.1.1

4. Have you ever used ethtool to troubleshoot your connection?

5.  Do you specifically need a static IP? Have you just tried to connect and receive a dynamic IP address first to verify that you can connect to your router/DHCP server?

---

### Post by dwdarkstar on 2008-02-29
[FONT="Book Antiqua"][SIZE="3"]Hey Kevdog!  Thanxs for taking a look.  I hope calling you out in the title of my post was not in bad taste, but I have been reviewing your How-To's and your posts for the last two weeks, and you seemed like the knowledgeable grinder who could help me.

1.)  So, if I do have access to the previous instillation, I'm not sure how to do it.  Since removing Dapper I have installed and reinstalled Gutsy, Hardy, and now Fiesty multiple times, and each time reformatting the entire disk, so I'm not sure about that one.

2.)  I ran dmesg and yes, there are errors but I think they are pertaining to my wireless driver bcm43xx_ which is depreciated and needs to be updated.  I can worry about this later after repairing my LAN.  Please see the results of dsmeg below; I attempted to filter out anything not related to networking.

3.)  I set the my default gateway as per your instructions:
[/SIZE][/FONT]
```
Z:~$sudo route add default gw 192.168.2.1
Z:~$
```
[FONT="Book Antiqua"][SIZE="3"]4.)  I have not used ethtool to trouble shoot my connection

5.)  No, I wouldn't say that I need a static IP, but it is something I now how to do, so thats how I always connect to my network.  I have not tried to connect and receive a dynamic IP address, but I have found instructions as too HOW at the following link:[/SIZE][/FONT]

[COLOR="Blue"]http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_use_dynamic_IP_addressing_for_your_host_using_the_free_DynDNS_service[/COLOR]

[SIZE="3"][FONT="Book Antiqua"]Would you like me to pursue this?



Thanks again for your help Kevdog, I really appreciate it.  My sister currently resides up in Nederland.  I'll be here until another graveyard shift later tonight and will try to keep an I out for your reply.[/FONT][/SIZE]


[SIZE="4"][FONT="Book Antiqua"][INDENT]results from dmesg[/INDENT][/FONT][/SIZE]
```
Z:~$dmesg

[   15.919025] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   15.919167] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   15.919520] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   15.919688] TCP: Hash tables configured (established 16384 bind 8192)
[   15.919692] TCP reno registered
[   17.145089] TCP cubic registered
[   17.145097] NET: Registered protocol family 1
[    6.596000] eth0: VIA Rhine II at 0x1d800, 00:40:45:18:95:8b, IRQ 11.
[    6.596000] eth0: MII PHY found at address 1, status 0x7869 advertising 05e1 Link 45e1.
[   22.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   23.824000] NET: Registered protocol family 17
[   24.920000] NET: Registered protocol family 23
[   24.964000] bcm43xx driver
[   26.088000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   26.132000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   26.144000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   26.152000] cs: IO port probe 0x100-0x3af: clean.
[   26.156000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.156000] cs: IO port probe 0x820-0x8ff: clean.
[   26.156000] cs: IO port probe 0xc00-0xcf7: clean.
[   26.156000] cs: IO port probe 0xa00-0xaff: clean.
[   28.088000] lo: Disabled Privacy Extensions
[   32.296000] Using specific hotkey driver
[   37.276000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   38.200000] eth0: no IPv6 routers present
[   40.284000] handlers:
[   40.284000] [<dc89ddd0>] (rhine_interrupt+0x0/0xb80 [via_rhine])
[   40.284000] Disabling IRQ #11
[   40.452000] ppdev: user-space parallel port driver
[   41.696000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.696000] apm: overridden by ACPI.
[   41.736000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   41.912000] Bluetooth: Core ver 2.11
[   41.912000] NET: Registered protocol family 31
[   41.912000] Bluetooth: HCI device and connection manager initialized
[   41.912000] Bluetooth: HCI socket layer initialized
[   41.980000] Bluetooth: L2CAP ver 2.8
[   41.980000] Bluetooth: L2CAP socket layer initialized
[   42.220000] Bluetooth: RFCOMM socket layer initialized
[   42.220000] Bluetooth: RFCOMM TTY layer initialized
[   42.220000] Bluetooth: RFCOMM ver 1.8
[   59.268000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   65.056000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   88.400000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   92.384000] NETDEV WATCHDOG: eth0: transmit timed out
[   92.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[   92.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  100.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  100.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  100.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  104.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  104.384000] eth0: Transmit timed out, status 0002, PHY status 786d, resetting...
[  104.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  113.128000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  116.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  116.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  116.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  132.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  132.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  132.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  136.352000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  159.576000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  284.404000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  358.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  358.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  358.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  376.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  376.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  376.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  392.384000] NETDEV WATCHDOG: eth0: transmit timed out
[  392.384000] eth0: Transmit timed out, status 0003, PHY status 786d, resetting...
[  392.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  407.632000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```
[SIZE="3"][FONT="Book Antiqua"]This cycle repeated about 10-20 times.[/FONT][/SIZE]

---

### Post by jcostom on 2008-02-29
Your output from dmesg, showing eth0 resets with PHY status 786d turned up this thread:

[http://ubuntuforums.org/showthread.php?t=586044](http://ubuntuforums.org/showthread.php?t=586044)

Check post #13 - looks like a possible fix for your troubles, as unlikely as it may appear at first.  The other guy has a similar card, not quite the same (r74 vs r78), but it may be bios-related.  I've always found those VIA ethernet chipsets to be twitchy..

Also, I assume your /etc/network/interfaces has something in it like:

auto eth0
iface eth0 dhcp

?

I also found this:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/35444](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/35444)

It suggests booting with "noapic".  I'd try that before horsing around with bios settings..

---

### Post by dwdarkstar on 2008-02-29
[FONT="Book Antiqua"][SIZE="3"]Hey Jcostom, thanxs for having a look.  I checked out the thread you suggested and there where definite similarities, however I am not very knowledgeable about BIOS settings and so would probably leave that as plan D or E.

The BUG victum you found also had similar hardware to me, but his trouble's occurred in Dapper, and Dapper for me was virtually trouble free and my LAN was very reliable.  So...I'm not sure.

Below are the components listed in /etc/network/interfaces:    [/SIZE][/FONT]

```
Z:~$sudo /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
ifacewlan0 inet dhcp

```

---

### Post by kevdog on 2008-02-29
id try editing your grub settings to boot with the noapic flag

---

### Post by dwdarkstar on 2008-03-01
[FONT="Book Antiqua"][SIZE="3"]Hey Kevdog, so I tried booting with noapic but this appeared to have no effect.  But you got me thinking and I searched the forums to find this little gem:

[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=609340&highlight=Averatec%2C+networking[/COLOR]

Post #3.  Amending my GRUB file to include **acpi=noirq**, save, reboot and [COLOR="Red"]PRESTO[/COLOR], full recognition and connection to wired network by DHCP.  I can't say that I fully understand exactly what I did, but I am certainly releived to be drafting this post on my laptop!

I have some downloading/enabling/personalizing to do; but when I find some spare time I think I will update my bcm43xx drivers and try to enable wireless using your HOW TO post.  Thanxs for your time Kevdog, you guys are the steady machete on this Unix safari.  [/SIZE][/FONT]

---

### Post by kevdog on 2008-03-02
If you could post your grub settings that would be great --- the actual file!

---

### Post by dwdarkstar on 2008-03-02
[SIZE="3"][FONT="Book Antiqua"]I would be happy to post the actual GRUB file.  Please find it below.  I have colored the additional code that was required to solve my networking issues in [COLOR="Red"]red[/COLOR].  The addition on line beginning with *# defoptions* insures the GRUB modification is applied every time you boot your machine.  Since applying this mod I have had no system freezes and have accessed the net on multiple wired networks using DHCP.  I hope anyone else struggling with an Averatec 3200 series laptop while using Feisty or Gutsy will find this post and try this fix.[/FONT][/SIZE]

```
Z:~$sudo gedit /boot/grub/menu.lst 


```

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=eba912fa-7ca7-4df1-9a34-a22fe2068142 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=**[COLOR="Red"]acpi=noirq[/COLOR]** quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eba912fa-7ca7-4df1-9a34-a22fe2068142 ro **[COLOR="Red"]acpi=noirq[/COLOR]** quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=eba912fa-7ca7-4df1-9a34-a22fe2068142 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eba912fa-7ca7-4df1-9a34-a22fe2068142 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=eba912fa-7ca7-4df1-9a34-a22fe2068142 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

### Post by Loosewheel on 2008-03-02
Hi guys,
Doesn't the pound sign at the beginning of a line cause it to be ignored?
(# defoptions=acpi=noirq quiet splash)
And, dwdarkstar, your 'ifconfig -a" output showed no IPv4 addresses.(no IPv6 either)
I believe that is because you tried to use static IP. And your last go round with DHCP is what made it work.
IMHO, networkmanager is the culprit. I run Ubuntu-7.10 x86_64, and can not set a static IP.
If I try, everything goes to heck. The resolv.conf  file is messed up and I can't edit the DNS or Domain fields in 'Network Settings'.

NetworkManager is a guess. I suspect it because when I installed it on a perfecly good PCLinuxOS system, it crashed. And a post on another forum said "the version of dhclient that PCL uses doesn't work with NM".

I still don't have things completely squared away yet....working on it.

---

### Post by dwdarkstar on 2008-03-03
[SIZE="3"][FONT="Book Antiqua"]Hey Loosewheel, I can't say for sure if a *#* comments out a line, but if you read the line before the default boot options begin you will see: [/FONT][/SIZE]

```
## DO NOT UNCOMMENT THEM, Just edit them to your needs
```

[SIZE="3"][FONT="Book Antiqua"]...so, I guess in this case it doesn't matter, just edit them to your needs.  In any case, with out adding that code to the* # defoptions* line, I lost my networking capabilities upon booting after the initial reboot, so I think you definitely need that line.[/FONT][/SIZE]

---

