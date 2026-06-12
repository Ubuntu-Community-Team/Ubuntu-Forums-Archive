---
title: "can't retrieve ip from dhcp"
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by jlagrone on 2007-08-22
I am unable to get an IP address from the local DHCP server.  I'm not quite sure what happened, but it seemed to have just stoped working a few days ago.  The only thing that I remember changing is removing vmware and the usual updates, but I don't think that is the problem since I have another computer exhibiting the same behavor.

Otherwise, at the time the issue first appeared, the machines were connected to a D-Link router and had been for at most a day or so.

Also, this appears to be happening on both wired and wireless connections.

here are some readouts that may or may not be useful, let me know if you need anything else.

Honestly, I think the problem is something with my university's network, but they claim it is my problem as they don't officially support linux.

```
dhclient eth0

Listening on LPF/eth0/00:15:c5:07:28:59
Sending on   LPF/eth0/00:15:c5:07:28:59
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:15:C5:07:28:59  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1821770 (1.7 MiB)  TX bytes:4764 (4.6 KiB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:22:53:3C  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:50 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x6000 Memory:ecfff000-ecffffff 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:07:28:59  
          inet addr:169.254.4.18  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1876 (1.8 KiB)  TX bytes:1876 (1.8 KiB)

```

```

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```

```
/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


```

---

### Post by A$h X on 2007-08-22
Looks like your router isn't handing out automatic IP addresses like it supposed to. Your machine can't even see your gateway (ie router) so you should start with a factory reset of the router. I had a D-link before and every few months it would forget all it's settings and need resetting and all the details re-entered. :-s

---

### Post by jlagrone on 2007-08-22
Right, I've experienced that also.  The problem is that it happens regardless of whether the computer is hooked up to the router or directly

---

### Post by A$h X on 2007-08-22
So it happens even if you have an ethernet cable from the socket to your machine? I would say that it a problem with the uni's network. Do you have access to a windows machine to confirm the problem lies with ubuntu? Preferably one you could try from your own room/socket just to be extra sure.

---

### Post by jlagrone on 2007-08-22
Well, my roommates laptop works on both of our ports, but mine is currently not working on either.  I have informed the uni IT guys, but of course they are denying that it is their problem.

I guess I'll just spend a lot more time complaining to them, maybe I'll find someone who will be willing to verify the situation.

---

### Post by A$h X on 2007-08-22
Okay try this: Click the network icon in the top right next to the speaker. click maunal configuration. Select static IP and enter the following:


IP address: 169.254.4.18
subnet mask: 255.255.0.0
gateway address: 169.254.4.1

If that doesn't work try changing the gateway to 164.254.4.0

Bear in mind this is a long shot as your network is automatically handing IP's and your making ubuntu stick to one which may cause a conflict in the future, but it's worth a try. Good luck.

---

### Post by jlagrone on 2007-08-22
I'd love to do that (I know it works, though with a different gateway and subnet) the problem is that the uni boots anyone who doesn't use their assigned ip off the network, so it only ends up complicating things.

Oh well, I guess I'll try some different dhcp clients and see if that works.  Then proceed to annoy the IT guys until they get around to taking a look at it

---

