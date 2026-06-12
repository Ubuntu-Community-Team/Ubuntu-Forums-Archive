---
title: "Ubuntu Server 16.04.1 on Hyper-V -- can't get networking up"
date: 2016-08-19
forum: Networking &amp; Wireless
---

### Post by nick-mueller41 on 2016-08-19
Hello all!
I'm trying to get a Ubuntu Server running in Hyper-V on Windows Server 2012 R2, and I can't quite get networking up.  The Windows Server 2012 R2 isn't running a DHCP server, so I need to use static IPs.

When I try to ping the Hyper-V Host, I get
```
xxx@xxxxx:~$ ping [hyper-v ip]
connect: Network is unreachable
```

Note that only "lo" shows up when I do a sudo ifconfig, but eth0 shows up with no inet address when i do a sudo ifconfig -a:
```
xxx@xxxxx:~$ sudo ifconfig -a
eth0 Link encap:Ethernet HWaddr [mac addr]
 BROADCAST MULTICAST MTU:1500 Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo Link encap:Local Loopback
 inet addr:127.0.0.1 Mask:255.0.0.0
 inet6 addr: ::1/128 Scope:Host
 UP LOOPBACK RUNNING MTU:65536 Metric:1
 RX packets:4 errors:0 dropped:0 overruns:0 frame:0
 TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1
 RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)
```

My interfaces looks like this:
```
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

#auto enp0s3
#iface enp0s3 inet dhcp
#auto br0

iface eth0 inet static
  address 10.5.130.184
  netmask 255.255.255.0
  gateway 10.5.130.254
#  bridge_ports eth0
#  bridge_fd 9
#  bridge_hello 2
#  bridge_maxage 12
#  bridge_stp off
```

As you can probably see i tried defining a bridge at the instruction of another post, but i'm not very familiar with bridges, and the network interfaces failed at startup because br0 wasn't found.  so i set br0 back to eth0 in the iface definition line.

My /etc/resolv.conf is:
```
nameserver 10.5.130.180
```
after editing the base file.

Not sure where to go from here.  Any thoughts?  I'm pretty sure the hyper-v server is set up correctly (e.g. the virtual switch is correctly shared to the clients) because my other clients (two opensuse VMs and one Win7 VM) are able to connect to the internet through this.

---

### Post by nick-mueller41 on 2016-08-19
NEVER MIND I FIGURED IT OUT.
Was just missing
```
auto eth0
```
from my interfaces.  :)

---

