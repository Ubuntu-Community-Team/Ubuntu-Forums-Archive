---
title: "Ethernet connects gets DHCP but wont send/recv any data?"
date: 2015-05-11
forum: Networking &amp; Wireless
---

### Post by 1yan on 2015-05-11
Hi, 

So I have this weird issue that suddenly started after a reboot one day, I assume that some update somewhere has broken it?
The adapter seems to be working it even gets its DHCP address but it wont send any data through.

I get nothing when I ping 8.8.8.8 or 10.1.6.1 (router) but if I ping its own 10.1.6.194 it responds.
also I cant ping it from my working computer.

ifconfig:
eth2 Link encap:Ethernet HWaddr 00:1f:bc:11:bf:1b
inet addr: 10.1.6.194 Bcast: 10.1.6.255 Mask: 255.255.255.0
inet6 addr: fe08::21f:bcff:fe11:bf1b/64 Scope: Link
UP BROADCAST RUNNING MULTICAST MTU: 1500 Metric:1
RX Packets: 47 errors: 0 dropped: 0 overruns: 0 frame: 0
TX packets: 405 errors:0 dropped:0 overruns:0 carrier:0
RX bytes:5761 (5.7 KB) TX bytes: 36056 (36.0 KB)
Interrupt:20 Memory: fb100000-fb120000

---

### Post by SeijiSensei on 2015-05-11
Please show the contents of "route -n".  Is the default gateway in 10.1.6.0/24?

---

### Post by 1yan on 2015-05-16
Thanks for the reply.

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.6.1        0.0.0.0         UG    0      0        0 eth2
10.1.6.0        0.0.0.0         255.255.255.0   U     1      0        0 eth2
192.168.88.0    0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

I was just playing with it and found if I plug a USB Ethernet in it works no problem.
The port is fine because the computer is dual booted with windows and doesn't have this issue with windows.

---

### Post by SeijiSensei on 2015-05-16
First, you have two networks assigned to the same device.  You should be using another interface for 192.168.88.0/24.  Does Windows have both network addresses active as well?

Where are eth0 and eth1?  Usually the primary Ethernet adapter is assigned eth0.  That's the one I normally connect to the upstream router.  

Plugging in another device probably resolves the conflict on eth2.

---

### Post by 1yan on 2015-05-16
I don't imagine so, I don't use 192.168.88 at all. I had a look around to find where it's getting that from but everything is set to automatic? Also should it not matter since the default is still 10.1.6.1?

My computer died a while back and rather than re-install I just put the hdd in a new computer. In the logs it shows up as eth0 when initialising then it renames it to eth2 because it still remembers the 2 devices on my old pc :P

and yes 192.168.88 isn't there on the usb adapter.

---

