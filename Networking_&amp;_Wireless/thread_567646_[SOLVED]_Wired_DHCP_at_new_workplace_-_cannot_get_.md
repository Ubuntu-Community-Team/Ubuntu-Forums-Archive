---
title: "[SOLVED] Wired DHCP at new workplace - cannot get connected"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by niltub on 2007-10-04
I have moved to a new workplace and the "IT support" is not particularly interested in getting my Ubuntu distribution connected to the internet (though was helpful in getting windows connected).  I was hoping that someone out there may be able to help.  I have a dual boot (windows xp / Ubuntu Feisty) Dell Latitude D600.  As a start (from browsing other threads on similar problems), the following commands issued the following output (and a big thanks to anyone taking the time to read it):

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:B6:B9:08  
          inet6 addr: fe80::20f:1fff:feb6:b908/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:113470 (110.8 KiB)  TX bytes:22971 (22.4 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0E:35:41:6A:F8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:395 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3149 (3.0 KiB)  TX bytes:21128 (20.6 KiB)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

eth0:avah Link encap:Ethernet  HWaddr 00:0F:1F:B6:B9:08  
          inet addr:169.254.5.124  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6522 (6.3 KiB)  TX bytes:6522 (6.3 KiB)

```

route

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         *               0.0.0.0         U     1000   0        0 eth0

```

sudo dhclient

```

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:1f:b6:b9:08
Sending on   LPF/eth0/00:0f:1f:b6:b9:08
Listening on LPF/eth1/00:0e:35:41:6a:f8
Sending on   LPF/eth1/00:0e:35:41:6a:f8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 137.111.180.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 137.111.180.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Thanks for your time, and hope someone out there can be a little more helpful than the "IT support".

---

### Post by kevdog on 2007-10-04
Do you have to do anything special for a windows connection??? Or is everything automatic dhcp assignment and gateway??

Can you list:
lshw -C network
lspci -nn

Thanks

---

### Post by niltub on 2007-10-04
Thanks for your interest.

I had to provide the 12 digit number that corresponds to the "hardware address" ( 00:0f:1f:b6:b9:08 ) to the IT support.  After that, I simply booted into windows, and it 'just worked', no additional fiddling around.  Unfortunately not the same in Ubuntu.

The output of "lshw -C network"

```

  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:b6:b9:08
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.72.1 duplex=full firmware=5705-v3.16 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:faff0000-faffffff irq:11
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:41:6a:f8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:fafef000-fafeffff irq:5

```

The output of "lspci -nn":
```

00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)

```

Thanks again.

---

### Post by noob12 on 2007-10-04
From the DHCP interaction 

```

Listening on LPF/eth0/00:0f:1f:b6:b9:08
Sending on   LPF/eth0/00:0f:1f:b6:b9:08
Listening on LPF/eth1/00:0e:35:41:6a:f8
Sending on   LPF/eth1/00:0e:35:41:6a:f8
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 137.111.180.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 137.111.180.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPREQUEST on eth0 to 255.255.255.255 port 67
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

It looks like you have both interfaces up and doing DHCP at once.  You actually get two offers presumably both on the wired.  I suggest that you keep your wireless down because it is interfering here.

This might be enough to get you running to begin with
```

sudo ifconfig eth1 down
sudo ifdown eth0
sudo ifup eth0

```

If you are using network manager, I'd suggest that you reduce your /etc/network/interfaces file to just the first stanza: keep the one that configures the lo (loopback) interface; remove the other ones.  Reboot.  See if things are better.

---

### Post by niltub on 2007-10-04
Thanks noob12 and kevdog.

Hmmm. OK. I am running network manager.  I have turned wireless off.  The /etc/network/interfaces file used to read:

```

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp




iface eth0 inet dhcp

auto eth0

```

If I reduced it to the first stanza, (auto lo / iface lo inet loopback), sudo ifdown eth0 and sudo ifup eth0 gave (respectively):

```

ifdown: interface eth0 not configured

Ignoring unknown interface eth0=eth0.

```

SO, I added in the lines about eth0 (auto eth0 / iface eth0 inet dhcp), but then I was back to the same problem as before.  Any ideas?

Thanks again ... hopefully this will work out in the end. I really don't want to have to get rid of Ubuntu.

---

### Post by kevdog on 2007-10-05
I think he means for now just comment out (#) every entry in the interfaces file except the lines with lo and eth0.  

Cycle the interface
sudo /etc/init.d/networking restart

Then can you manually connect at work
sudo ifdown eth0 
sudo ifup eth0
sudo dhclient eth0

Your MAC address of your card isnt any different than the MAC address you gave the IT people (so they can perform some MAC filtering) so this shouldnt be a problem.

---

### Post by niltub on 2007-10-05
Thanks Kevdog,

The commenting and restart command are a lot easier.  Yes, I kind of latched on to the importance of the hardware address, and had checked that the number was the same, so I'm a bit baffled as to what is actually wrong.  Commenting all but the lo and eth0 sections in /etc/network/interfaces so that the uncommented lines read:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

and then typing sudo /etc/init.d/networking restart, gives the output:

```
 * Reconfiguring network interfaces...
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:1f:b6:b9:08
Sending on   LPF/eth0/00:0f:1f:b6:b9:08
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

which to my eyes looks pretty similar to what I had before (to my no-network-knowledge brain), but perhaps someone with a better trained eye can spot the problem (or point me in the direction of where the problem might be).

Thanks again for your help - truly fantastic to know there are people out there willing to part with a little time to make my life a little easier.

---

### Post by noob12 on 2007-10-05
They are similar but different.  In your last manual attempt, you got no DHCP offers. 

On the prior attempt that you had posted you had actually gotten the normal offers:  once on the discover phase and once on the request phase, which would normally have succeeded, but I think the second DHCP sequence on eth1 running at the same time screwed it up.

The reason the commands I suggested didn't work was because you followed the /etc/network/interfaces cleanup suggestions first rather than after them; I expected you to do things in the order that you read them, so I had put those instructions after the commands.   Anyway, as you saw, once you remove the configurations of  those interfaces from /etc/network/interfaces, the ifup, ifdown commands and /etc/init.d/networking will no longer operate on them, but NetworkManager still will.  They are considered in "roaming mode".  I'd still recommend doing that for a laptop.  

Remove or comment out all but the loopback section from /etc/network/interfaces.

After that,  Plug in to the net, reboot and login.  Check network manager to see that networking is enabled and the wired network is selected.

See if you just get a connection automatically that way.  If not, post the output of these commands:

```

# We want to see if you have a link.  You did earlier, but not sure in your last
# attempt
sudo ethtool eth0

# See if you got partial success with an address
ifconfig -a

# Routes?
route -n

# DNS?
cat /etc/resolv.conf

# We'll see the dhclient messages here
tail -15 /var/log/syslog

# May see a problem here
tail -15 /var/log/kern.log

```

---

### Post by niltub on 2007-10-08
Sorry, have been offline partially because of the very problem I am writing about.  It all seems to be getting quite complicated for someone that has no idea about networking.  You may have been right about the order in which I was doing things.

I'll close the thread for now, because unfortunately I don't have the time at the moment to be addressing the problem... back to windows, for now.

Thanks very much for your help though!  Hope to back sometime with Ubuntu when there is time to delve into all this complicated stuff.

---

### Post by sageb1 on 2007-10-08
This issues is not SOLVED for the OP. Rather, he has indicated that he is a newbie with regard to networking at the command line so as to not be overwhelmed by the learning curve. This is why he set up his laptop's hard drive for dual boot!

[B]FWIW I may suggest to the OP to spend time at home at his convenience studying the HOWTO for networking.  You have plenty of tools on the net to help you, including wikipedia and Google.  It is NOT COMPLICATED; rather, most newbies to Linux loathe command-line troubleshooting "because of all the keyboard entry".
[/B]

YMMV:guitar:

---

### Post by niltub on 2007-10-08
I'm not entirely a newbie - I have been using Ubuntu for the last two years.  I'm not afraid of the command line, and have used it on numerous occasions.  For myself, the problem is less to do with command line editing, and more to do with the fact I have NO idea about networking, so I don't really know what I am doing on THAT side of things.

Unfortunately I don't have the time for extended searching / troubleshooting at the moment (I actually have work to do :) ).  Sorry to disappoint.  Don't worry, I plan to come back at it sometime in the (hopefully not overly distant) future when I actually do have time - I like Ubuntu.  It's just the old problem that it's not what everyone else uses, at least in the places I have worked.

---

