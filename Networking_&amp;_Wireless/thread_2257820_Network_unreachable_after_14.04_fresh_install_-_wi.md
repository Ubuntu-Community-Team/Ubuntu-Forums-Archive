---
title: "Network unreachable after 14.04 fresh install - wired"
date: 2014-12-22
forum: Networking &amp; Wireless
---

### Post by drifting_along on 2014-12-22
I installed 14.04 and was able to do plenty of regular software updates and could connect to the internet normally at first.  I only use a wired connection.  I had 12.04 installed on the same machine, same hardware and ethernet cable, and never had network issues.

Now when I boot up it looks like I connect at first but it sometimes will not connect to my router.  Sometimes everything works ok, and when I look at the routing table there are entries, and I can successfully make HTTP requests, but then my connection will be dropped and those entries in the routing table will just disappear.  When I attempt to add an entry to the routing table at that point I get "Network unreachable."  My router is at 192.168.1.1 and when I lose my connection I cannot ping that address.  More info:

```

$ uname -mr
3.13.0-39-generic x86_64

```

```

$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 74:27:ea:4c:b9:cf
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:53 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff

```

```

$ route
### This is the table when I have a good connection ###
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router.asus.com 0.0.0.0         UG    0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 74:27:ea:4c:b9:cf  
          inet addr:192.168.1.85  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7627:eaff:fe4c:b9cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:225 errors:0 dropped:0 overruns:0 frame:0
          TX packets:542 errors:0 dropped:94 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81224 (81.2 KB)  TX bytes:88594 (88.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3300 (3.3 KB)  TX bytes:3300 (3.3 KB)

```


```

contents of /etc/network/interfaces:
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

What else can I do to troubleshoot this?

Thanks!

---

### Post by r.stiltskin on 2014-12-22
Judging by /etc/network/interfaces it looks like you have tried to manually configure your network (I don't think the last 2 lines are normally used in 'buntu 14.04).  So, did you also disable or uninstall Network Manager?  Because if you have manual settings and also Network Manager (the gui network setting tool accessed in Settings Manager) both trying to manage your connections that is likely to cause trouble.

Then if you still have trouble I guess it might be helpful to see the results of those commands (lshw, route and ifconfig) when it's NOT working.

---

### Post by drifting_along on 2014-12-23
I commented out the last two lines in /etc/network/interfaces and things seem to be working fine now.

Thanks r.stiltskin!

---

