---
title: "baffled with wlan0 (or lack of) - yet another wireless question"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by libertarian on 2007-06-10
Hi Folks,

Before we proceed here is my setup :
AMD 64
ASUS Av8-E delux
using the MRV8K50.inf files from ASUS and NDISWRAPPER version:
```

ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko
version:        1.46
vermagic:       2.6.20-16-generic SMP mod_unload

```

A list of loaded modules yeilds the following:
```

 ndiswrapper -l
mrv8knt : driver installed
        device (11AB:1FA7) present

```

```

lspci | grep Lib
00:07.0 Ethernet controller: Marvell Technology Group Ltd. 88W8310 and 88W8000G [Libertas] 802.11g client chipset (rev 07)

```

I have recently upgraded from 6.06 to 6.10 and then straight to Feisty.  Before my wireless connection used to work fine and I had a script that I ran to make it kick in :
```

#! /bin/bash
ifconfig wlan0 up
iwconfig wlan0 key 3E63F57BEC0BE662498C40BDBF
iwlist wlan0 scan
iwconfig wlan0 ap 00:11:D8:A1:78:56
iwconfig wlan0 channel 7
iwconfig wlan0 essid WANADOO-C580
ifconfig wlan0 192.168.1.199
dhclient wlan0
#dhcpcd wlan0

```

Performing ifconfig produces the following:
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:D8:A1:65:B1  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fea1:65b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3404802 (3.2 MiB)  TX bytes:578440 (564.8 KiB)
          Interrupt:36 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:797 (797.0 b)  TX bytes:797 (797.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:11:D8:A1:78:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Memory:da010000-da020000 

wlan0:ava Link encap:Ethernet  HWaddr 00:11:D8:A1:78:56  
          inet addr:169.254.7.51  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:da010000-da020000 

```

The wlan0 appears which is great, but I have never EVER noticed what the wlan0:ava before,  it is assigned to  an ip address which is in teh wrong range.  Interestingly this appears on the windows machine too when the wireless connect under windows.  However it doesnt work.

```

QUESTION: how do I make the wlan0 work properly as when I run my script there seems to be an issue with leasing an ip address.

```

```

/sams/etc/init.d/wireless
wlan0     Scan completed :
          Cell 01 - Address: 00:0E:9B:A3:09:6C
                    ESSID:"WANADOO-C580"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:39/100  Signal level:-71 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
There is already a pid file /var/run/dhclient.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:11:d8:a1:78:56
Sending on   LPF/wlan0/00:11:d8:a1:78:56
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13

```

Has anyone come across this and know how to fix it,  would be greatly appreciated.

---

### Post by libertarian on 2007-06-10
Also,  can someone explain what an access point is.  Is it the MAC address of the wirelesscard or is it the MAC address of the router?

:p

---

### Post by libertarian on 2007-06-12
:confused:

---

### Post by libertarian on 2007-06-12
Please can someone help ...

:confused:

---

### Post by kevdog on 2007-06-12
Please post the following:

/etc/iftab
dmesg

---

### Post by dbott67 on 2007-06-12
The 'ava' comes from Avahi.

[http://en.wikipedia.org/wiki/Avahi_(software](http://en.wikipedia.org/wiki/Avahi_(software))

It utilizes similar technology as APIPA (which Microsoft uses) whenever a DHCP server cannot be reached:

[http://www.webopedia.com/TERM/A/APIPA.html](http://www.webopedia.com/TERM/A/APIPA.html)

As for the actual problem, your wlan0 is not obtaining an IP address from the DHCP server, so the Avahi system assigns it the 169.254.x.y address.  The problem could be related to a number of things from driver to the version of ndiswrapper, etc.

Post the output that kevdog asked for as well as:
```
sudo lshw -C network
```

---

### Post by libertarian on 2007-06-15
Hi Dbot67,

sorry about the delay in coming back to you,  I guess I lost hope on my wireless...

Here is the output from what you requested:

```

sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 15
       serial: 00:11:d8:a1:65:b1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.105 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:d9000000-d9003fff ioport:b000-b0ff irq:36
  *-network
       description: Wireless interface
       product: 88W8310 and 88W8000G [Libertas] 802.11g client chipset
       vendor: Marvell Technology Group Ltd.
       physical id: 7
       bus info: pci@00:07.0
       logical name: wlan0
       version: 07
       serial: 00:11:d8:a1:78:56
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8knt driverversion=1.47+Marvell,11/16/2004,2.7.1.2 latency=32 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:da000000-da00ffff iomemory:da010000-da01ffff irq:17

```

I hope that this can give you some insight in solving this problem as it has me baffled.  Also it seems that the access point doesn't become associated somehow,  Even when I assign it manually?  Can you help?

---

### Post by libertarian on 2007-06-15
Also kevdog,   when I do the following,  it doesn't work...

```

/etc/iftab
bash: /etc/iftab: Permission denied

```

This is when I am root.

Any ideas?

---

