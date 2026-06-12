---
title: "Realtek 8139 weirdness"
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by CptnSbaitso on 2005-10-11
Howdy all,
     Long time Windows user, short time Linux user, first time Ubuntu user.  Heard so many good things that I had to give it a try.

I've got Ubuntu freshly installed on a PII 350 machine.  It's running a very basic setup, including a Realtek 8139 PCI network card.  However, after configuring it, I can't get any network communication in or out.  Packet sniffers on the cable show nothing leaving the box and even ifconfig counters show the lo interface is getting the traffic while eth0 stays silent.  I can see the card running lspci:

```
[snip]
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[snip]

```
ifconfig looks good (you can see that all traffic is ending up in lo):
```
eth0      Link encap:Ethernet  HWaddr 00:A0:D2:1D:02:03  
          inet addr:192.168.1.254  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d2ff:fe1d:203/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xb400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:561366 (548.2 KiB)  TX bytes:561366 (548.2 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

added the defaut gateway (even though it's ping inside the local subnet that are failing).  Here are my routes:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

/etc/network/interfaces reads as follows:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.254
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

I feel like I am missing something really simple.  Any traffic I try simply fails.  Pings return "From 192.168.1.254 icmp_seq=* Destination Host Unreachable". Broadcast pings only get replies from myself, not any of the other hosts on the network (which are pingable from other hosts).  Please don't let something this stupid ruin Ubuntu for me.  :-)

Thanks in advance!
-- CptnSbaitso

---

### Post by mlomker on 2005-10-11
I wonder if you're having the same problem that is documented in [this thread.]("http://www.ubuntuforums.org/showthread.php?p=377332#post377332")

---

### Post by CptnSbaitso on 2005-10-11
mlomker,

I do not recall seeing that error, but I will check through the logs first thing tomorrow.  It seems as though they are reporting issues with the driver not loading.  The driver seems to be loading for me, just not working the way I think it should.

Thanks for the quick reply!
CptnSbaitso

---

### Post by mlomker on 2005-10-11
> The driver seems to be loading for me, just not working the way I think it should.


Actually that thread documents the wrong driver loading--there are two different 8139 cards and it seems like the kernel sometimes misdetects which driver to load.

---

### Post by skoal on 2005-10-12
Howdy Captn,

It looks like you're using a router @192.168.1.1?

Is it possible you've assigned a static IP to this linux box, but are assigning dhcp in the router to other hosts, possibly assigning x.x.x.254 to another box from that pool?

I set a static IP in my router based on my MAC address, and changed nothing else in my Ubuntu configs. I still use 'dhcp' too, but the router is smart enough to just reserve a static address for my MAC and remove that entry from the pool.

I'll post back the same information you did once you tell me that network topology and the hosts you have attached to it...

By the way, in my experience, x.x.x.1 and x.x.x.254 are reserved for certain devices, like the router itself (and excluded from use) - which is why your router is using x.x.x.1.  My router uses x.x.x.254, and my statically reserved IP from the DHCP pool is x.x.x.150 (which I picked). Maybe change your static IP for your Realtek NIC to something like 150 instead.

\\//_

---

### Post by CptnSbaitso on 2005-10-12
skoal,
     > It looks like you're using a router @192.168.1.1?
     Yeah.  The router is a Linksys box using 192.168.1.1.
     > Is it possible you've assigned a static IP to this linux box, but are assigning dhcp in the router to other hosts, possibly assigning x.x.x.254 to another box from that pool?
     All hosts are statically assigned.  The only other host on the network is a laptop using 192.168.1.100.  The Ubuntu box is running 192.168.1.254 since the plan is to replace the Linksys router (and it's lovely security holes) as well as to serve files and printers, probably DHCP as well.  If there were IP address conflicts, I would think I'd be able to see the ARP requests from the packet sniffer and an error in dmesg.  However, I don't see those at all.
     > I'll post back the same information you did once you tell me that network topology and the hosts you have attached to it...
     As far as the network topology goes...  The Internet comes into the WAN port of the Linksys box.  Then two devices (a laptop running XP and the Ubuntu box) are plugged into the built-in switch.  That's it!  :-)  Nothing fancy.
     I will try switching everything over to DHCP just for fun, but I don't understand why that would fix it.  (Still, worth a shot!).  I'll post back a little later today.

Thanks for the idea,
CptnSbatiso

---

### Post by CptnSbaitso on 2005-10-12
all,
     Well, I feel stupider.  :-)  Cable tester showed that the cable between the Ubuntu box and the switch were bad.  The giveaway was in the dmesg log:

```
eth0: link down
```

This must have been the reason why all packets were being routed through lo instead of eth0, as ifconfig was reporting.  As soon as I got a good cable in there:

```
eth0: link up, 10Mbps, half-duplex, lpa 0x0000
```

And of course, traffic is now happy.  So remember kids, check your dmesg early and often.

Thanks for all your help,
-- CptnSbaitso

---

### Post by someonestolecc on 2007-10-14
posted in wrong thread doh

---

