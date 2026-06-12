---
title: "Wired connection in Network Manager and eth0 interface disappeared"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by obik on 2008-04-22
hello, I am new here and have a problem with my wired connection. recently it  just disappeared :/ I think it could happen while unsuccesfull hibernation. I was trying to search solution but every one found failed.

my ifconfig
> 
ath0      Link encap:Ethernet  HWaddr 00:16:E3:5E:CD:27  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:fe5e:cd27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43339606 (41.3 MB)  TX bytes:2607137 (2.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-5E-CD-27-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:279784 errors:0 dropped:83788 overruns:0 frame:94874
          TX packets:14766 errors:24 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:85874891 (81.8 MB)  TX bytes:2940128 (2.8 MB)
          Interrupt:18 



does someone know what is wifi0 and why its mac is so weird?

/etc/network/interfaces :
> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


/etc/init.d/networking restart:
> 
* Reconfiguring network interfaces...
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth0.


help please.

---

### Post by Iowan on 2008-04-22
Wish I could check my system... otherwise my guess is even wilder.  Might try killing the process 134519120, then restarting networking again.

---

### Post by obik on 2008-04-22
This didn't worked.
bash: kill: (134519120) - No such process

---

### Post by Iowan on 2008-04-22
Do you actually have wireless - or is something being misinterpreted?

---

### Post by muximus on 2008-04-22
try the following:

```
ifdown eth0
```

then, 
```
ifup eth0
```

---

### Post by obik on 2008-04-22
> **Iowan said:**
> Do you actually have wireless - or is something being misinterpreted?

Yes I have wireless, the problem is about wired.

my ifdown eth0 says:
ifdown: interface eth0 not configured

---

### Post by Iowan on 2008-04-24
More things to check:```
lspci
``````
ifconfig -a
``````
dmesg |grep eth
```

---

### Post by obik on 2008-04-25
lspci:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
09:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

ifconfig -a:
ath0      Link encap:Ethernet  HWaddr 00:16:E3:5E:CD:27  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e3ff:fe5e:cd27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11774 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21841954 (20.8 MB)  TX bytes:1997372 (1.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:900 (900.0 b)  TX bytes:900 (900.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-16-E3-5E-CD-27-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:324573 errors:0 dropped:85906 overruns:0 frame:447815
          TX packets:12561 errors:24 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:51755134 (49.3 MB)  TX bytes:2291136 (2.1 MB)
          Interrupt:18 

and no reply from "dmesg |grep eth" :(
thanks for interest.

---

### Post by jtrindle on 2008-04-25
Your wired Ethernet controller is not appearing in lspci, which is ominous...

Is there a setting in the CMOS (BIOS) setup when the computer first starts to disable on-board peripherals?  Maybe it got disabled in the hibernation problem you had.

What kind of computer is it?

---

### Post by obik on 2008-04-25
it's toshiba satellite l100 laptop. I will check this setting in bios right away.

EDIT:there are some settings for LAN. it's "Built-in Lan" option which was enabled when I checked.

---

### Post by shredder12 on 2008-10-15
i am having exactly the same problem..earlier it was working fine..i even downloaded a 80 Mb update of something called linux kernel generic..and then after it i turned it off..and when i came back after a few hours and turned on the system..i found that the same problem..
anyone having some idea about it..

---

### Post by ub0fan on 2009-05-17
this didn't work for me

---

### Post by Iowan on 2009-05-18
This thread is probably a couple of versions old... what didn't work?  I've discovered the new "rfc3442-classless-static-routes" caused my laptop to fail to receive a DHCP address. More info [here]("http://ubuntuforums.org/showthread.php?p=7280398#post7280398").

---

### Post by s1500 on 2009-05-18
> **Iowan said:**
> This thread is probably a couple of versions old... what didn't work?  I've discovered the new "rfc3442-classless-static-routes" caused my laptop to fail to receive a DHCP address. More info [here]("http://ubuntuforums.org/showthread.php?p=7280398#post7280398").

I would like to try that fix, but I never found the .conf file in question on my system.

---

### Post by Iowan on 2009-05-19
> **s1500 said:**
> I would like to try that fix, but I never found the .conf file in question on my system.Sorry, that got corrected a couple of posts later in the thread - it should be */etc/dhcp3/dhclient.conf*.

---

### Post by s1500 on 2009-05-20
Well, a quick update.

Tried to install an Ethernet card(as opposed to using the onboard one). Linux didn't even see it. 

Resetted the bios. Saw the onboard one again. NetworkManager naturally failed on it, but running dhclient seemed to do the trick.

After reserving an IP address on the router, I can even access it by name on other machines. Samba still doesn't work, but with samba, it breaks as so much as you look at it wrong.

Wireless works great, but not a solution. The Network Manager icon STILL thinks I'm completely disconnected, and doesn't really think I have an ethernet card to begin with. So it goes.

---

### Post by jtarin on 2010-07-12
> **jtrindle said:**
> Your wired Ethernet controller is not appearing in lspci, which is ominous...


lspci lists ```
09:04.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)
```

---

### Post by Iowan on 2010-07-12
Closed.
Very old thread...

---

