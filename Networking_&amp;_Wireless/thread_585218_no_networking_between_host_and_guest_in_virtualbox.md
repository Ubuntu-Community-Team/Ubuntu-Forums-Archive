---
title: "no networking between host and guest in virtualbox"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by go_beep_yourself on 2007-10-21
I am trying to do some networking with the guest os and host os in Virtual box. I am unable to ping or ssh from the host to the guest.

This is eth0 on the host
```

$ sudo ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:14:2A:BD:89:A2  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:febd:89a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4664862 errors:10 dropped:0 overruns:0 frame:10
          TX packets:4677190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3348243647 (3.1 GB)  TX bytes:561228538 (535.2 MB)
          Interrupt:20 Base address:0xa000 
```

Here's some pictures of the problem.

[img]http://img48.imageshack.us/img48/9164/networking2xe5.png[/img]

[img]http://img48.imageshack.us/img48/722/networkingkr4.png[/img]

---

### Post by techpr on 2007-10-21
Perfect timing... same problem

Last night I installed Debian Etch as Guest on Ubuntu 7.04 Host.
want to connect via SSH.

---

### Post by Hero of Time on 2007-10-21
Read the VirtualBox manual. You need to set a host interface for your guest OS. Create a new network interface and bind that to your VM.

---

