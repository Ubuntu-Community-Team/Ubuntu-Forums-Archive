---
title: "activate ethernet?"
date: 2006-12-23
forum: Networking &amp; Wireless
---

### Post by jonkanon on 2006-12-23
I recently installed Ubuntu on my compaq laptop and everything works fine except for network connections. I cannot access internet nor ping my router.

The strange thing is, considering this picture that I found on the internet as I tried to solve the problem on my own, that I lack the buttons "Activate" and "Deactivate". On my screen, they are simply not there. Why is that?

[IMG]http://www.livecd.hu/files/livecd.hu/images/Ubuntu-Network-Settings_0_0.png[/IMG]


My ifconfig looks like this:

eth0      Link encap:Ethernet  HWaddr 00:02:A5:B6:C5:91 
          inet6 addr: fe80::202:a5ff:feb6:c591/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:13122 (12.8 KiB)

lo        Link encap:Local Loopback 
          inet addr: 127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8288 (8.0 KiB)  TX bytes:8288 (8.0 KiB)

--

But the only connection listed in my "connection properties" is "lo".

you should also know that my isp requires dhcp.

I'm writing now from a mac that is on the same router so there's no problem there.

I'd be grateful for all help!
merry christmas!

maybe I should add that the cable is checked and that I get stable green and yellow lights.

---

### Post by scrooge_74 on 2006-12-23
command line

sudo ifdown eth0
sudo ifup eth0

also sudo dhclient

Check on the forums there is a similar thread out there I read a few days ago, just don/t remember which one, probably on beginers talk


good luck

---

### Post by jonkanon on 2006-12-23
Hi scrooge, thanks.

I already tried that. I also did the "tulip" fix, with no progress.
I read lots of threads before I decided to post here.

I have an eth0, so hardware seems fine... I simply seem to be getting no DHCP offers? Is that right?
How does this look?

--

jon@jon-laptop:~$ sudo ifdown eth0
Password:
There is already a pid file /var/run/dhclient.eth0.pid with pid 4570
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:b6:c5:91
Sending on   LPF/eth0/00:02:a5:b6:c5:91
Sending on   Socket/fallback


jon@jon-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:b6:c5:91
Sending on   LPF/eth0/00:02:a5:b6:c5:91
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


jon@jon-laptop:~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:a5:b6:c5:91
Sending on   LPF/eth0/00:02:a5:b6:c5:91
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


--

I have an eth0, so hardware seems fine... I simply seem to be getting no DHCP offers. Is that right?

Suggestions? Please.
regards

---

### Post by scrooge_74 on 2006-12-23
Check if there are any drivers you can download for your ethernet card

or try looking any bug reports for your specific ethernet card.  I cant think of a reason why it can communicate.

Also try rebooting your router, that have given me problems in the past

---

### Post by dbott67 on 2006-12-23
What's the output of **sudo lshw -C network**?

---

### Post by dbott67 on 2006-12-23
You can also try the following:

1. Replace ethernet cable with known working cable (switch with the Mac, if possible).
2. Re-boot the router (the DHCP server could be stalled/hung)

-Dave

---

### Post by jonkanon on 2006-12-24
The output is:

jon@jon-laptop:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:02:a5:b6:c5:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=full firmware=N/A link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:40100000-40100fff ioport:2800-283f irq:11


--

(I reboot the router about all the time and I have tried changing cables)

thanks

---

### Post by jonkanon on 2006-12-27
Hi again.

I tried another router. On this other router, internet works.

Perhaps the problem was my Zyxel router then.

Thanks for your posts.

---

