---
title: "[SOLVED] Need help with wireless on Dell Inspiron 1505"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by deNoobius on 2008-06-21
I've tried all the advice I can find on this forum, including using ndiswrapper to install a fresh driver for the wireless card and editing the network interfaces file, but the wireless connection just won't work (I'm using a wired connection now).  I'm a noob (cf. my user name!) and am at wit's end.  Any help from those more experienced much appreciated.

Thanks.  Details:

The command ~$ sudo lshw -C network gives the following (note the "Network DISABLED" statement near the end):

*-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5a:d3:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.4 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:8c:9b:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

ifconfig gives me (keeping in mind that I'm wired in):

eth0      Link encap:Ethernet  HWaddr 00:19:b9:5a:d3:cb  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe5a:d3cb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1106140 (1.0 MB)  TX bytes:260689 (254.5 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83700 (81.7 KB)  TX bytes:83700 (81.7 KB)

And the network interfaces file reads as follows:

auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

---

### Post by deNoobius on 2008-06-22
OK, found a possible clue.  I went back to the live CD, and it identified a missing piece of firmware, which I installed.  Then, voila!  I had wireless networking--all the nearby networks were visible, and I was able to log onto mine and access the Internet, use Firefox, etc.

However, when I removed the live CD and rebooted from the hard drive, I was back to the same non-wireless status (also, oddly, my sound stopped working, and again, it was fine with the Live CD).  

Would a reinstall from the live CD be indicated?  If so, will I be able to save my Windows partition (which I still need for some purposes)?  

Thanks.

---

### Post by deNoobius on 2008-06-24
Anyone?

---

### Post by pokipoki08 on 2008-06-24
Use sypnatic to remove Network Manager (including the gnome counterpart) and wicd.

Try these commands at the terminal & post the output here

```
dmesg | grep ndiswrapper
ndiswrapper -l
```

```
dmesg | grep wlan
cat /var/log/messages | grep wlan
```

```
ifconfig
cat /etc/network/interfaces
```

```
iwlist wlan0 scan
iwconfig wlan0
```

Are you trying to connect to an encrypted wireless network? Is it WEP or WPA?

---

### Post by deNoobius on 2008-06-24
Thanks for the reply.  Yes, the network is encrypted with WEP, but I don't think that's the issue.  First, when I connect with a cable, the encryption isn't a problem.  Second, I turned the encryption completely off and still had the same problem.

Here are the answers to the terminal commands--any clues?

:~$ dmesg | grep ndiswrapper
:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:5a:d3:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

eth0:avahi Link encap:Ethernet  HWaddr 00:19:b9:5a:d3:cb  
          inet addr:169.254.9.221  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56652 (55.3 KB)  TX bytes:56652 (55.3 KB)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth0

stephen@stephen-laptop:~$ iwlist wlan0 scan
wlan0     No scan results

~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ayuthia on 2008-06-24
Can you also post your lshw -C network?  The information you posted in your earlier post should now be different since you have installed NDISwrapper.

---

### Post by pokipoki08 on 2008-06-24
Your wireless adapter is not picking up any wireless network at all.

Please run each of these commands at the terminal & post the output here
```
dmesg | grep ndiswrapper
```
```
dmesg | grep wlan
```
```
cat /var/log/messages | grep wlan
```
```
uname -mar
```

---

### Post by deNoobius on 2008-06-25
Thanks.

Here is the result of lshw -C network:

  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:5a:d3:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.5 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:19:7d:8c:9b:73
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Still showing network as DISABLED.  (The card is ENABLED in the BIOS, I already checked that).

---

### Post by deNoobius on 2008-06-25
The output of the set of commands from Popkipoki08 is:

Linux stephen-laptop 2.6.24-19-386 #1 Wed Jun 4 15:54:02 UTC 2008 i686 GNU/Linux

---

### Post by deNoobius on 2008-06-27
Solved, kind of.  All my playing around hosed my Windows partition (luckily everything is backed up), so I just reinstalled Ubuntu on the entire disk.  I then reinstalled b43-fwcutter, which was the firmware the Live CD identified, and voila, my wireless network appeared.

I'm finding the computer to be clean, quick, and fast, which is great.  If I decide to reinstall Windows, I may do so via Parallels or a similar solution.

Thanks to everyone who responded.

---

