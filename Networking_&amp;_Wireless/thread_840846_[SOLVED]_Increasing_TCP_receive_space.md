---
title: "[SOLVED] Increasing TCP receive space"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by x1a4 on 2008-06-25
Hi,

How do I increase TCP's receive space?  I tried using FreeBSD's method by setting the net.tcp.recvspace kernel parameter (and various variations) but Linux doesn't have that.  

Any ideas?

Thank you.

---

### Post by x1a4 on 2008-06-27
Figured it out.  The Linux kernel has the following TCP/Net options.  The values are what I came up with for my system.  If you want to change these make sure to do your homework and find values which are optimal to your system and Internet connection. 
```

net.core.rmem_default = 256960
net.core.rmem_max = 16777216
net.core.wmem_default = 235116
net.core.wmem_max = 16777216
net.ipv4.tcp_rmem = 5120 256960 16777216
net.ipv4.tcp_wmem = 5120 235116 16777216

```
*rmem_* receive memory space
*wmem_* send memory space

I added these to /etc/sysctl.conf and executed ```
sysctl -p
``` to make the changes permanent.
When I was testing I executed ```
sysctl -w *option*=*value*
```

I also optimized my connection a little by changing values for my Ethernet card using **ifconfig** like so:
```
ifconfig -v eth0 mtu 1492 txqueuelen 1024
```
MTU or Maximum Transmission Unit is the size (in bytes) of the largest packet.  On my connection 1492 is the largest packet I can have without fragmentation.

txqueuelen is the length of the transmit queue, increasing this relieves congestion--if you have a slow connection set this to a lower value.

---

