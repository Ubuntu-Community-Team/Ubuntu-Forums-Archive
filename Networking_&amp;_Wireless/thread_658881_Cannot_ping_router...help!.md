---
title: "Cannot ping router...help!"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by medleykupps on 2008-01-05
Hi,

I'm having a problem pinging my router.  I'm new to Linux & was wondering if someone could help...?

```

medley@medley:~$ ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data
From 169.254.11.57 icmp_seq=2 Destination Host Unreachable
From 169.254.11.57 icmp_seq=3 Destination Host Unreachable
From 169.254.11.57 icmp_seq=4 Destination Host Unreachable

--- 10.1.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3003ms, pipe 3

medley@medley:~$ ifconfig -a
eth0      Link encap: Ethernet  HWaddr 00:11:D8:6D:EA:E8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:24

eth0:avah Link encap: Ethernet  HWaddr 00:11:D8:6D:EA:E8
          inet addr:169.254.11.57  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:24

lo        Link encap:Local Loopback
          <snip>

wlan0     Link encap:Ethernet  HWaddr 00:11:D8:6D:ED:40
          inet6 addr:  fe80::211:d8ff:fe6d:ed40/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
          RX packets:90 errors:0 dropped:0 overruns:0 frame:0
         TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:14061 (13.7 Kib)  TX bytes:468 (468.0 b)
          Interrupt:26 Memory:dc010000-dc020000
 
medley@medley:~$ route
Kernel IP routing table
Destination    Gateway       Genmask            Flags  Metric Ref     Use Iface
link-local      *        255.255.0.0           U     0        0      eth0
default        *        0.0.0.0                   U     1000   0      eth0

```

Cheers in advance...!

---

### Post by Predator[23rd] on 2008-01-05
type **sudo ifconfig eth0 10.1.1.100** and try again ...

---

### Post by Dark Hornet on 2008-01-05
from your ifconfig output, you do not have a valid IP address applied to any of your interfaces...this is why you cannot ping your router.

---

### Post by sdide on 2008-01-05
What is the output of (with sudo or as root)
# dhclient eth0

---

