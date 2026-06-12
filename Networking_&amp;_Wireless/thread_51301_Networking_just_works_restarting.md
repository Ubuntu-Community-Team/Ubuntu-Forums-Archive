---
title: "Networking just works restarting"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by azambuja on 2005-07-23
Hello,

I have properly configured my network with two cards, eth0 and eth1. It works fine, connects to the net, all the stuff. When I reboot, networking starts but im offline. Then i simply restart networking without changing a configuration bit, and it starts working.

Networking its starting on boot, but only when i restart it it works.

Anyone can help?

Thanks

---

### Post by azambuja on 2005-07-26
i cant believe no one in the forum can help me :-(

---

### Post by gruepig on 2005-07-26
Post the contents of /etc/network/interfaces.  Also the output of '/sbin/ifconfig -a' and 'route -n' when you are offline.

---

### Post by azambuja on 2005-07-26
[QUOTE=gruepig]Post the contents of /etc/network/interfaces.  Also the output of '/sbin/ifconfig -a' and 'route -n' when you are offline.[/QUOTE]

thanks for trying to help :-)

here it is:
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 10.100.100.254
netmask 255.255.255.0
gateway 10.100.100.254

auto eth1

auto eth0

ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:02:B3:29:8C:83
          inet addr:200.236.36.137  Bcast:255.255.255.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:434070 (423.8 KiB)  TX bytes:684 (684.0 b)

eth1      Link encap:Ethernet  HWaddr 00:40:F4:61:76:99
          inet addr:10.100.100.254  Bcast:10.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe61:7699/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:3 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:900 (900.0 b)  TX bytes:900 (900.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.100.100.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
200.236.36.0    0.0.0.0         255.255.254.0   U     0      0        0 eth0
0.0.0.0         10.100.100.254  0.0.0.0         UG    0      0        0 eth1
0.0.0.0         200.236.36.1    0.0.0.0         UG    0      0        0 eth0

all this offline.

i wait for for more help :-)

cheers

---

### Post by gruepig on 2005-07-27
I don't think your configuration for eth1 makes sense.  You're using 10.100.100.254 for both your IP address and your gateway.  What do you mean by that?  I don't think you want to have the same address for your IP and your gateway.  Further, 10.100.100.254 is also your broadcast address (as I think the last IP address on the subnet is used as the broadcast address by default).

If what you want is for this box to route (NAT) all traffic from 10.100.100.0/24 out eth0, try using 10.100.100.1 for your address (assuming you haven't used it elsewhere) and omit the gateway line entirely.  Good luck!

If that doesn't fix it, try running 'ifdown eth0; ifdown eth1'  followed by 'ifup eth0' so that you have eth0 up but not eth1.  Can you ping 200.236.36.1 (and beyond)?  Similarly, bring up just eth1 and see if you can ping other 10.100.100.0/24 hosts (if you have any)?

---

