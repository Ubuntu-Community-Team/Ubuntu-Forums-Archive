---
title: "USB to Ethernet adapter support in Ubuntu Fiesty"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by garethc on 2007-04-25
I have a 'no name' ethernet to usb adapter based on the admtek/infineon adm8511 chipset. XP recognizes the adapter, but Ubuntu does not. Does Ubuntu support any ethernet to usb adapters? Can I get this adapter to work somehow under Ubuntu so I can have internet connectivity? These adapters are not too common in the West, but quite common here in Thailand where I am now. Anyone with any ideas please post!!

cheers,
gc

---

### Post by spd106 on 2007-04-26
This most comprehensive site for USB devices is probably this one [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)
It lists an ADMtek device that uses the pegasus driver.

Do you get any messages in dmesg when you insert the device? or in the /var/log/syslog?

---

### Post by tgui on 2007-05-02
Ive got the same.

Relevant dmesg:
```
[423795.288000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[423795.472000] usb 3-1: configuration #1 chosen from 1 choice

```

I'd love to get it working. Anyone have hints?

---

### Post by garethc on 2007-05-03
thanks for the reply... nope, have had no luck so far. what is strange is that when connected, the usb ethernet adapter does seem to come up as a network adapter, although i don't have enough experience with ubuntu to dig deeper and see what the problem is. the device is not recognized by name, and i can't give any more info because i went back to windows xp for the time being (feelings of guilt arise :-0)

i'll pop in the live cd and see if i can't get any more info... cheers!!

---

### Post by garethc on 2007-05-03
On SourceForge.net --

Linux Pegasus USB-Ethernet drv --> project

 The idea is to get all pegasus and pegasus II based usb-ethernet devices to work under linux. That simple. :)

Project Admins: petkan
Operating System: All POSIX (Linux/BSD/UNIX-like OSes), Linux
License: GNU General Public License (GPL)
Category: Linux

Hope they make some headway and get a driver(s) out!

---

### Post by garethc on 2007-05-03
ok,

it seems i was wrong. according to dmesg the adapter is being recognized correctly and an appropriate driver is being loaded, the adapter is initializing as eth1. the problem seems to be that no network address can be resolved, ip address et al. are all 0.0.0.0 -- this is when i wish i knew more about networking in ubuntu! i'll be doing some research, but if spd106 or other power users have any advice i'd definitely appreciate it!

the problem is probably small, but still too large for my infantile knowledge of linux ;-)

some appropriate dmesg output:

[   88.676000] pegasus: v0.6.14 (2006/09/27), Pegasus/Pegasus II USB Ethernet driver
[   88.776000] pegasus 2-1:1.0: setup Pegasus II specific registers
[   88.880000] NET: Registered protocol family 17
[   88.896000] pegasus 2-1:1.0: eth1, ADMtek ADM8511 "Pegasus II" USB Ethernet, 00:08:54:e2:61:cc
[   88.896000] usbcore: registered new interface driver pegasus

---

### Post by garethc on 2007-05-03
ok,

i did a little research and came up with some commands that should produce feedback relevant to my predicament. considering the nature of the thread has changed somewhat, i will also be posting this as a new thread in the same forum (networking & wireless). i'll be following both threads... hopefully someone can interpret this stuff for me!! muchos gracias! keep in mind that the adapter in question is eth1...

'sudo ifconfig' gives:

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:07:10:B2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 

eth1      Link encap:Ethernet  HWaddr 00:08:54:E2:61:CC  
          inet6 addr: fe80::208:54ff:fee2:61cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5052 (4.9 KiB)

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:07:10:B2  
          inet addr:169.254.5.111  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:22 

eth1:avah Link encap:Ethernet  HWaddr 00:08:54:E2:61:CC  
          inet addr:169.254.8.215  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3796 (3.7 KiB)  TX bytes:3796 (3.7 KiB)

```

'sudo dhclient eth1' gives:

```
Listening on LPF/eth1/00:08:54:e2:61:cc
Sending on   LPF/eth1/00:08:54:e2:61:cc
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

'sudo tcpdump -vvn -i eth1' gives:

```
tcpdump: WARNING: eth1: no IPv4 address assigned
tcpdump: listening on eth1, link-type EN10MB (Ethernet), capture size 96 bytes
12:59:51.004121 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
12:59:58.003907 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, secs 7, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:00:05.003950 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, secs 14, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:00:19.004014 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0xadd28c61, secs 28, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:06:40.001962 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:06:43.001802 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, secs 3, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:06:51.001962 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, secs 11, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]
13:07:01.001929 IP (tos 0x10, ttl  64, id 0, offset 0, flags [none], proto: UDP (17), length: 328) 0.0.0.0.68 > 255.255.255.255.67: BOOTP/DHCP, Request from 00:08:54:e2:61:cc, length 300, xid 0x78a1621, secs 21, Flags [ none ] (0x0000)
          Client-Ethernet-Address 00:08:54:e2:61:cc [|bootp]

8 packets captured
8 packets received by filter
0 packets dropped by kernel

```

** note that i CTRL+C'd the tcpdump process after ab out 2 minutes because it seemed to be in a loop giving similar data over and over - was I wrong to cancel?!

---

### Post by garethc on 2007-05-03
oh, forgot to post /etc/network/interfaces --

```
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
iface wlan0 inet dhcp
```

---

### Post by gradedcheese on 2007-05-03
FYI, the Linksys M100 and M200 (or maybe the 'M' goes after the numbers) adapters work perfectly, as do the Netgear ones.  They use the 'asix' chip, which is fully supported.

---

### Post by garethc on 2007-05-04
I don't think the driver is the problem, i think it's the horrid apartment building firewall/proxy I'm stuck behind here. For some reason, under Ubuntu the "negotiation" for an IP assignment just isn't happening. In XP, the browser brings up the proprietary "log in" screen for internet access automatically. Not so under Ubuntu. I'm not sure what to do about that!

cheers,
g

---

