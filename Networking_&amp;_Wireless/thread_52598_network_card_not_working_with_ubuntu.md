---
title: "network card not working with ubuntu"
date: 2005-07-28
forum: Networking &amp; Wireless
---

### Post by cloudr on 2005-07-28
I have  Compaq Deskpro 6350 with a PCI network card.
The card is ok because it works in Windows (as soon as I get the network card working wiht ubuntu, windows goes for good)

Windows XP reports the card as Fast Ethernet Compaq NC3121

lscpci reports the card as:
Ethernet controller: Intel Corp. 82557/8/9 [Ethernet Pro 100] (rev 05)

ifconfig eth0 reports the cards's MAC address.

A static ip gets assigned and then shows under ifconfig properly except it doesn't work. trying to ping a host brings " connect: Network is unreachable"

If set to DHCP if just reports the network is down.

/etc/network/interfaces:
auto lo
iface lo inet loopback
mapping hotplug
script grep
mat eth0
iface eth0 inet dhcp


I tried also with a wireless usb card and same problem.
Module was loaded, MAC address identified but it wouldn't work with static of DHCP address.

It seems like networking is not working properly. This is an out of the box ubuntu 5.04 (as it has never been succesfully connected to the internet nothing out of the default instalation has been installed except the driver zd1211 for the wireless card)

I will be happy to get just the wired network card working.

Any help greatly appreciated. If somebody needs extra info I will be happy to get it.

---

### Post by gruepig on 2005-07-28
Run 'ifdown eth0' to make sure your ethernet interface is down.  Then run 'ifup eth0' to bring it back up.  Do you get any errors?  What does 'ifconfig -a' show?  If you are using DHCP, are you getting an IP address (and broadcast address, subnet mask)? What is the output of 'route -n'?  If you are using a static configuration, what are you using for IP address, etc.?  Can you ping your own IP?

---

### Post by cloudr on 2005-07-28
ifdown eth0 followed by ifup eth0 ->

There is already a pid file /var/run/dhclient.eth0.pid with pid 24641422
[This above I fixed minutes laterby deleting /var/run/dhclient* so no longer shows, the rest of the output stayed the same]
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:08:d7:a9:a7:c3
Sending on   LPF/eth0/00:08:d7:a9:a7:c3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
send_packet: Network is down

----------------------
ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:D7:A9:A7:C3
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6339 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:353220 (344.9 KiB)  TX bytes:353220 (344.9 KiB)

sit0      Link encap:IPv6-in-IP v4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---------------
route -n  ->
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
--------------
I can ping localhost and 127.0.0.1
In ubuntu I never get a DHCP lease from the router. The leds on the router are on  including the link one where the cat5 cable is plugged. Under windows the card gets a lease normally from the same router (although under Windows other things don't work which work great under Ubuntu)

I don't know if it helps but the Compaq Deskpro 6350 has the PCI slots mounted on a 'daughter board' that plugs on a huge slot on the motherboard.

---

### Post by gruepig on 2005-07-29
Is it possible that you already have a DHCP process running?  Run 'ps aux | grep dhcp' to see.

---

### Post by cloudr on 2005-07-29
output of ps aux | grep dhcp

dhcp    4676 0.0 0.1    2296  1128 ?     S<s 07:09  0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0

I have plugged (temporalily) a USB network card to the same PC and same router and it works fine both with DHCP or a static IP.

Now I have assigned a static IP to the Compaq NC3121.

ifdown eth0 brings:
ifdown: interface eth0 not configured

then ifup eth0 brings:
SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Failed to bring up eth0


ifconfig doesn't show eth0 (but shows correctly the working USB card as eth1)
ifconfig -a shows eth0 as:
eth0  Link encap:Ethernet HWaddr 00:08:D7:A9:A7:C3
      inet addr:192.168.1.251 Bcast:192.168.1.255 Mask:255.255.255.0
      BROADCAST MULTICAST MTU:1500 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 frame:0
      collisions:0 txqueuelen:1000
      RX bytes:0 (0.0 b)   TC bytes:0 (0.0 b)

ping 192.168.1.251 seems to work normally.

eth1 gets an aditional line starting with inet6 addr: fe80::xxx:xxxx: ...

---

