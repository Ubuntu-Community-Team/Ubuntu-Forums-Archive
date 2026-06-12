---
title: "Wired connection works but no IPv4 assigned"
date: 2014-03-11
forum: Networking &amp; Wireless
---

### Post by tommy-merchant1 on 2014-03-11
Hey, so, I am having problems with Ubuntu 12.04 and connecting to my router using Ethernet(Happens with every router I have tried).
My computer does connect to the router but doesn't assign an IPv4 address.
Output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 94:de:80:cf:fc:77            inet6 addr: fe80::96de:80ff:fecf:fc77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:1385 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:342 (342.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:999951 (999.9 KB)  TX bytes:999951 (999.9 KB)


lxcbr0    Link encap:Ethernet  HWaddr d6:a9:a0:a4:50:b8  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::d4a9:a0ff:fea4:50b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:10419 (10.4 KB)


wlan0     Link encap:Ethernet  HWaddr c0:4a:00:17:2c:65  
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c24a:ff:fe17:2c65/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17297 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10313148 (10.3 MB)  TX bytes:3568354 (3.5 MB)
```
I don't exactly know what the problem is but I can't seem to find a solution. (The router BTW is the same one as I am connected on with the wlan0 interface but I am using a not working very well wireless dongle that cuts out every 2 seconds and I want to use an Ethernet connection).
Before it wouldn't work at all until I set IPv6 to link local only, I don't know what other info to put here, please help.

---

### Post by chili555 on 2014-03-11
What is *lxcbr0*? It seems to have an IP address. Is it this?> 

On many Linux distributions, the LXC package will install startup scripts that pre-configure a bridge (basically, a software virtual switch) for use with LXC.

LXC is a set of tools for working with Linux's infrastructure for jails/zones/sandboxes. It builds on the same APIs used by Android to sandbox applications, for example. Some people use it for a lightweight linux-on-linux virtualization, but it is not the same thing as type 1 or type 2 hypervisors at all.

If you don't know what LXC is, it most likely got installed along with something else, such as virt-manager, which requires libvirt, which often requires LXC.
Is this a virtual machine or...what?

---

### Post by tommy-merchant1 on 2014-03-12
> **chili555 said:**
> What is *lxcbr0*? It seems to have an IP address. Is it this?Is this a virtual machine or...what?
lxcbr0 is an interface registered by lxc, I believe it allows internet use from within an LXC box.
This isn't in a virtual machine but since I am on 64 bit linux I had to install wine using LXC.
The interface that the Ethernet connection is attached to is eth0.
So no, I am not inside a virtual machine this is a regular terminal.

---

### Post by chili555 on 2014-03-12
I'm sorry; you are far beyond my shallow area of expertise. Are you using Network Manager? We might try to get NM to ignore lxcbr0 and only manage eth0.

---

### Post by tommy-merchant1 on 2014-03-12
> **chili555 said:**
> I'm sorry; you are far beyond my shallow area of expertise. Are you using Network Manager? We might try to get NM to ignore lxcbr0 and only manage eth0.
Yes I am using Network Manager.

---

