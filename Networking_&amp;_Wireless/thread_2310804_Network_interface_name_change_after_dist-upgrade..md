---
title: "Network interface name change after dist-upgrade."
date: 2016-01-22
forum: Networking &amp; Wireless
---

### Post by Henrik_LIndstrm on 2016-01-22
So here's the story :).

Yesterday i made a dist-upgrade on my ubuntu server running 15.10. Im using the machine as a router, firewall, webserver and such tasks. But when i rebooted the whole NAT thing had stopped working and i started to investigate.

The first thing i realised was that my network interfaces now had the names eth0, rename1 and rename2. Before the kernelupdate the interfaces was named "enp1s6" and "enp3s0".

This is odd because Before this iv'e tried to rename them to eth0 and eth1 via /etc/systemd/network/ but did not get it to work. 

Adding this to /etc/udev/10-network.rules seems to have fixed the names for the physical network cards:

```

SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="1c:af:f7:70:ef:6c", NAME="wan0"
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="20:cf:30:1b:96:62", NAME="lan0"

```

I havn't found out how to rename the loopback device since it has no hw-address. 

This is how my 'ifconfig' looks now:

```

lan0      Link encap:Ethernet  HWaddr 20:cf:30:1b:96:62
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe1b:9662/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9099 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1563751 (1.5 MB)  TX bytes:2256104 (2.2 MB)
          Interrupt:40


rename1   Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:219 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:20800 (20.8 KB)  TX bytes:20800 (20.8 KB)


wan0      Link encap:Ethernet  HWaddr 1c:af:f7:70:ef:6c
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1eaf:f7ff:fe70:ef6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5568172 (5.5 MB)  TX bytes:3451994 (3.4 MB)
          Interrupt:21


```

Now Everything works but i don't feel safe because i don't know why one interface was called eth0 and the other ones rename1-2. And i also don't know how to fix this so now i'm asking the Community for some advice! 

So my questions are:


[LIST]
[*]How do i rename the rename1 (lo) interface to lo again?
[*]Any clues why my interfaces was renamed in the first Place?
[*]Will this happen every dist-upgrade?
[*]Is the solution to rename the interface via udev bulletproof? Will it work even if the kernel feels like renaming them again?
[/LIST]

Thanks in advance!

---

### Post by Bucky Ball on 2016-01-22
Welcome. Is your network connection working? If so, I'd forget about all this. 15.10 is known to rename network devices. Normal. This is 15.10 specific. No, it doesn't normally happen after every dist-upgrade.

Wouldn't worry about trying to rename everything. If it ain't broke, don't fix it. There is no problem here if your network connection is working as it should.

Note: If you are using Network Manager, any changes you make in /etc/network/interfaces don't make any diff.

---

### Post by Henrik_LIndstrm on 2016-01-22
> **Bucky Ball said:**
> Welcome. Is your network connection working? If so, I'd forget about all this. 15.10 is known to rename network devices. Normal. This is 15.10 specific. No, it doesn't normally happen after every dist-upgrade.

Wouldn't worry about trying to rename everything. If it ain't broke, don't fix it. There is no problem here if your network connection is working as it should.

Note: If you are using Network Manager, any changes you make in /etc/network/interfaces don't make any diff.

It's working again. Everything seems fine, and if i get you right i can feel safe with my new UDEV renaming of the interfaces. And i also found out how to rename the loopback interface. Thanks for the help!

---

