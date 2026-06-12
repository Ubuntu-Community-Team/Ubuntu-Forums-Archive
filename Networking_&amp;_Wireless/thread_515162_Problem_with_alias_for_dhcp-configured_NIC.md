---
title: "Problem with alias for dhcp-configured NIC"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by blametheduck on 2007-08-01
Hi all.

I have two machines running Ubuntu 7.04 configured by dhcp of a DSL router. Because I can't configure the dhcp address distribution on the router, I'd like to set up an alias for the NIC eth0.

I can do that on the command line and it works:
> sudo ifconfig eth0:0 192.168.4.7 up

Result here:
> 
#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:09:C1:8E:76
          inet addr:192.168.4.102  Bcast:192.168.4.255  Mask:255.255.255.0
          ...snip...

eth0:0    Link encap:Ethernet  HWaddr 00:11:09:C1:8E:76
          inet addr:192.168.4.7  Bcast:192.168.4.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17


Now I try to do it via /etc/network/interfaces:
> 
# cat /etc/network/interfaces

auto eth0
iface eth0 inet dhcp

auto eth0:0
iface eth0:0 inet static
address 192.168.4.7
netmask 255.255.255.0
network 192.168.4.0
broadcast 192.168.4.255
gateway 192.168.4.1


And it just doesn't work. The alias does not show up in ifconfig. Any ideas? What is really strange, is that this very configuration works on my laptop running Debian 4.0.

Feel free to comment on the general approach, e.g. whether it is sensible to use aliases or whether there's a better way to achieve the same goal.

Thanks in advance,
Frank

---

### Post by noob12 on 2007-08-01
I can't answer the sensibility question, but I did try this in my /etc/network/interfaces as a test and it worked for me.   I'm running 7.04 as well.  

I tested using **/etc/init.d/networking restart** and **ifup -a** and they both worked.  I was using eth4 and eth4:0 in my test, but I don't think that should make a difference.  The real interface was dhcp configured in my test as well.

---

### Post by blametheduck on 2007-08-02
Hi.

Thanks for sharing your experience. At first, I thought that I just overlooked something but when I tried ```
/etc/init.d/networking restart
``` I got the following error: ```
SIOCSIFFLAGS: Cannot assign requested address
```.

Further digging revealed that there are other people, experiencing the same problem:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/95968](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/95968)

The question remains why it works for you and why it doesn't work for other configurations?

Hm, so much for today...
Frank

---

### Post by noob12 on 2007-08-02
Maybe it is specific to eth0.  I'll try that when I get a chance.

EDIT:
I re-read [https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/123773)
more carefully.  **It says you get the message but the interface then comes up fine.**

When I did it in my test, I don't recall seeing any errors and the interface comes up.

---

### Post by noob12 on 2007-08-04
Confirmed that on my desktop with eth0, it gives me the 
**SIOCSIFFLAGS: Cannot assign requested address** error, but still comes up.

---

