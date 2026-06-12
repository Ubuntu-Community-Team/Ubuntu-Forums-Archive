---
title: "wired connection not working in hardy or vista"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by slowferrari on 2008-09-25
ok, i'm seriously confused. i just got my road runner hooked up at my new place and i went to plug it in and start internetting but i couldn't access any pages. the computer says i have a wired connection, but other than that, it's not working. i checked lshw and network is NOT unclaimed. it shows an Attansic L1 Gigabit Ethernet Adapter (rev b0), which is using the atl1 driver.

However, when i pull up the connection info through the network manager it shows no ip, or anything else. it does list that i am connected to a wired connection though. vista, however dosen't even show that a wired connection is available.

I am totally new to linux and ubuntu but i can follow directions, and I wont be able to figure this out on my own, none of the other posts i have looked at describe the same problem (note: network is NOT unclaimed, but isn't working). please help!

seriously, please help.

---

### Post by pytheas22 on 2008-09-25
Let's first try to rule out some variables:

1. Is this network card new?  If so, and you've never been able to connect using this computer before, then perhaps it's just a case of hardware failure.  Can Vista at least see that a networking device exists (if you look at hardware information)?

2. Are you sure that your RoadRunner connection works and that it's supposed to serve you a dynamic (dhcp) IP address?  Have you ever used it?  You say that you just got RoadRunner installed, so I wonder if something wasn't installed correctly by them and there's a problem with the connection itself, or with your cable modem.  If you can't get any computer to connect in any operating system but you're sure that it's not hardware failure, then I'd call RoadRunner and say that the connection doesn't appear to work.

If you don't think that any of the above is at fault, you can try to fetch an IP address in Ubuntu by typing:
```

sudo dhclient eth0
```

What is the output of that?

---

### Post by 4partee on 2008-09-25
Do you have any evidence that your new connection works? 

What is the output from 'ifconfig -a'?

---

### Post by slowferrari on 2008-09-25
i know the network card worked before i installed ubuntu, i was running xp originally and i was able to run a lan connection. its the integrated lan on the mobo, so i don't think its hardware failure per se. however, i know the connection is good, i'm using it on my eee (running eee ubuntu), it fires up right away no drama.

i'll plug the tower back in and fetch that output right now.

---

### Post by slowferrari on 2008-09-25
dhclient-->

There is already a pid file /var/run/dhclient.pid with pid 7133
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:f3:9d:be:94
Sending on   LPF/eth0/00:18:f3:9d:be:94
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

ifconfig-->

eth0      Link encap:Ethernet  HWaddr 00:18:f3:9d:be:94  
          inet6 addr: fe80::218:f3ff:fe9d:be94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:295 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:1262086 (1.2 MB)  TX bytes:53365 (52.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:17:3f:4f:d1:7e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1131 dropped:5 overruns:0 frame:1124
          TX packets:2084 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:88401 (86.3 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:18:f3:9d:be:94  
          inet addr:169.254.9.178  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:136240 (133.0 KB)  TX bytes:136240 (133.0 KB)


...and i'm totally lost

---

### Post by pytheas22 on 2008-09-25
I think we will have to look a little more in depth...

Please post the output of:

```
dmesg | grep -e eth0 -e eth1
lshw -C Network
lspci -nn
```

Also, do you have two ethernet cards in this computer?  Or one ethernet, one wireless?

---

### Post by slowferrari on 2008-09-26
i have an integrated lan, thats the gigabit connection. i also have a belkin usb stick that i use when there is no ethernet available. i have used it plug and play with no issue for months. I've tried unplugging it and turning off wireless and everything, though.

dmesg-->

[   54.430971] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[   68.518055] eth0: no IPv6 routers present
[  150.849116] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  161.319436] eth0: no IPv6 routers present
[  210.604663] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  211.570376] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  213.641573] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  213.682804] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  214.639056] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  224.633451] eth0: no IPv6 routers present
[  485.513293] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  495.955717] eth0: no IPv6 routers present
[  618.168411] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[  629.116118] eth0: no IPv6 routers present
[  889.959522] atl1 0000:02:00.0: eth0 link is down
[ 1212.784832] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[ 1212.787466] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1223.510879] eth0: no IPv6 routers present
[ 1846.261881] atl1 0000:02:00.0: eth0 link is down
[ 3677.309721] zd1211rw 5-8:1.0: eth1
[ 3677.509829] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3749.525747] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3753.982430] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 3754.015566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[16985.450333] atl1 0000:02:00.0: eth0 link is up 100 Mbps full duplex
[16985.453159] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[16996.266941] eth0: no IPv6 routers present
[17420.967607] atl1 0000:02:00.0: eth0 link is down

lshw-->

  *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:18:f3:9d:be:94
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1 driverversion=2.0.7 firmware=N/A latency=0 module=atl1 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:3f:4f:d1:7e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b/g

lspci-->

00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)

.. I'm still lost, i hope you guys understand what all this means...
is there a good resource to learn this stuff from?

---

### Post by 4partee on 2008-09-26
<slowferrari;5857100]i know the network card worked before i installed ubuntu, i was running xp originally and i was able to run a lan connection. its the integrated lan on the mobo, so i don't think its hardware failure per se.>

I agree.  Your hardware s/b ok.

<however, i know the connection is good, i'm using it on my eee (running eee ubuntu), it fires up right away no drama.>

I'll assume that your eee is wireless, so that means you have a wireless router, right?  

The router is the logical point of failure.  Using your eee, take a look at your router and see if it is denying your other computer to connect.  You might try doing a factory reset as most of these routers are quite open out of the box.

---

### Post by pytheas22 on 2008-09-26
I agree with the poster above that you should check the router.  I googled a bit and can't seem to find anyone else having trouble with your particular hardware, and since it works neither in Ubuntu nor Windows, it seems quite unlikely that it's a software problem on Ubuntu's part.

If possible, you may want to unplug your router and try connecting your computer directly to the ethernet connection.  Even though the router works for wireless connections, there could still be a problem (either hardware or software) with its wired ports, which you could bypass by hooking up directly to the outside connection.

Also, can you connect your eee using ethernet (if these things even have ethernet cards; not sure)?  If not, then that would further suggest that the problem is your router.

You could also try using a different ethernet cable, just in case the one you have is shot (not likely, but possible).

---

### Post by slowferrari on 2008-09-27
so, there was never a router involved. i don't own one.

the ethernet cable is fine, too. it's plugged into my eee.

i've done quite a bit of digging and my computer seems to be working fine, other than the wired lan connection. but ubuntu recognizes the adapter and even sees that i have a cable plugged in. of course, roadrunner is insisting that the problem must be with my computer. does anyone have any suggestions? there must be something i can try.

---

### Post by slowferrari on 2008-09-27
SOLVED

i went to micro center and bought a 20 dollar netgear 10/100 ethernet card. the modem is only 10/100 and i got a switch to go with it for 10 bucks. thanks for all your help though.

---

### Post by pytheas22 on 2008-09-28
Sorry that you ended up having to spend more money, but I'm glad to hear that you're online now.

I do suspect that there's just a hardware problem with your ethernet card.  The only way to know for sure would be to try to plug into someone else's network.  If it fails there as well, I'd make a big bet that the card is just shot or something, since it doesn't want to work either in Windows or Ubuntu.

---

