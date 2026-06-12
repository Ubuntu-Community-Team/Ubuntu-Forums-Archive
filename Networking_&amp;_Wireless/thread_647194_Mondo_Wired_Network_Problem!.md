---
title: "Mondo Wired Network Problem!"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by talltex02 on 2007-12-22
I am running Kubintu Gutsy. When I was away at school, my network connection worked fine, but now that I am at home for the Christmas break I cannot connect.   My router will not assign me an IP address. My brother is running Ubuntu Gutsy and can access the network.  This is why I am perplexed.

Here is a copy of my /etc/network/interface
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

# The second network interface
auto eth1
iface eth1 inet dhcp

# The third network interface
auto eth2
iface eth2 inet dhcp

# The wireless network interface
auto wlan0
iface wlan0 inet dhcp

auto ath0
iface ath0 inet dhcp

```

any help is greatly appreciated.

---

### Post by PreviousN on 2007-12-22
Ok, how about this:

Can you post your "ifconfig", ifconfig -a, and "route -n" 's results? THen, do a "ping google.com" and tell me the error. If it says no route, that could be something you would fix with the "route" command, or etc. 

Also, please note that these commands are for a wired network. If you're on a wireless network, try iwconfig. 

:-) Cheers -

---

### Post by talltex02 on 2007-12-22
Thank you for the help.

```

twitchy@***:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:76:61:00:12
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:04:5A:4D:A6:14
          inet6 addr: fe80::204:5aff:fe4d:a614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:2
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1826 (1.7 KB)
          Interrupt:21 Base address:0xd000

eth0:avah Link encap:Ethernet  HWaddr 00:0C:76:61:00:12
          inet addr:169.254.2.118  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x4000

eth1:avah Link encap:Ethernet  HWaddr 00:04:5A:4D:A6:14
          inet addr:169.254.4.156  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1876 (1.8 KB)  TX bytes:1876 (1.8 KB)

``````

twitchy@***:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:76:61:00:12
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0x4000

eth1      Link encap:Ethernet  HWaddr 00:04:5A:4D:A6:14
          inet6 addr: fe80::204:5aff:fe4d:a614/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:12 dropped:0 overruns:0 frame:17
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:1826 (1.7 KB)
          Interrupt:21 Base address:0xd000

eth0:avah Link encap:Ethernet  HWaddr 00:0C:76:61:00:12
          inet addr:169.254.2.118  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0x4000

eth1:avah Link encap:Ethernet  HWaddr 00:04:5A:4D:A6:14
          inet addr:169.254.4.156  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:21 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1876 (1.8 KB)  TX bytes:1876 (1.8 KB)

ra0       Link encap:UNSPEC  HWaddr 00-12-17-83-8D-EB-00-00-00-00-00-00-00-00-00-00
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0_ren Link encap:Ethernet  HWaddr 00:12:17:83:8D:EB
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

``````

twitchy@****:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0         U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0         U     0      0        0 eth1
0.0.0.0            0.0.0.0         0.0.0.0                U   1000   0        0 eth1

```

---

### Post by PreviousN on 2007-12-23
Try this:

1. Open a terminal.

 ```
  sudo ifconfig eth0 down && sudo ifconfig eth1 down 
```

This brings both interfaces down. I'm essentially getting you to start from scratch. 

2. In the same terminal...

```
 sudo ifconfig eth0 up && sudo ifconfig eth0 192.168.1.111 netmast 255.255.255.0 
```

This brings interface 0 up. I'm assuming this is the interface you have the cable plugged into. Then, after its up, it is assigned to 192.168.1.111 in the netmask 255.255.255.0. I'm assuming you've got a standard linksys/generic broadcom router. These usually have 192.168.1.1 as the GW. If you use a router that you configure on a different address (ie: 192.168.10.1, or 10.0.0.1, then give your computer an address on that subnet. So if you were on 192.168.10.1, the ifconfig comand above would be "192.168.10.111 netmask 255.255.255.0". 

Now, you've got interface 0 assigned to an address of 192.168.x.x, in the netmask 255.255.255.0. But where's your dns/gateway?!

3. In another terminal...

```
sudo route add default gw 192.168.1.1
```

This adds the default gateway as 192.168.1.1. Essentially, you should now be able to "ping" computers on your local network, or google!

So, this is of course a temporary fix. You may also want to try running this in a terminal if the above steps don't work:

```
sudo dhclient
```
This tells your computer to try to get an ip from a dhcp server again. It doesn't work for me always, but this could help you out. 

Hope these kind of helped. I know they're not a perminant solution, but hey, I gave it my best shot :-)

Cheers!

---

### Post by talltex02 on 2007-12-24
No dice :(

---

### Post by PreviousN on 2007-12-24
Whats' the error message when you do a "ping google.com"? If it says "no route to host", try pinging google.com on another computer, and grabbing the ip address. Then, on the broken computer, try pinging the ip address that you got. If that works, then its a problem with dns. 

Maybe someone else can give this guy a shot at help? I'm kinda out of ideas...

---

### Post by talltex02 on 2008-01-14
Thank you  for your help PreviousN.

The problem is solved.

I feel quite sheepish, but it was the cable.

---

