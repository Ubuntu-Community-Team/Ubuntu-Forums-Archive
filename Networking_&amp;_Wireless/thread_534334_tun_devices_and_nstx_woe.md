---
title: "tun devices and nstx woe"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by benevans55 on 2007-08-25
Hi there,

Im trying to setup a DNS tunneling experiment using [http://thomer.com/howtos/nstx.html](http://thomer.com/howtos/nstx.html) NSTX

I'm using Ubuntu 7.04

I need to create a tun0 virtual interface like this one from the how to..

tun0      Link encap:UNSPEC  HWaddr XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX-XX
          inet addr:10.0.0.1  P-t-P:10.0.0.1  Mask:255.0.0.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

However if I use tunctl to create the tun0, it does not have the magic P-t-P stuff. It looks like a regular interface. 

How do I create appropriate tun0 devices?

The really annoying thing is that I actually had the right tun0s on both my test systems, which must have been created by in the past by something or other, then when I clean installed to try and fix some other problems, no tun0s!!! Damn. This is driving me mad, I've been trying to find a solution for two days :-(

Thanks.

Ben

---

### Post by weblordpepe on 2008-04-16
Oh hai!

After going **apt-get install tun****modprobe tun** you may want to enter into **/etc/network/interfaces** the text:
> 
iface tun0 inet static
  address 10.0.0.1
  netmask 255.0.0.0

How on earth do I set up IP forwarding in the kernel with iptables??  Im trying to get this running also.

---

