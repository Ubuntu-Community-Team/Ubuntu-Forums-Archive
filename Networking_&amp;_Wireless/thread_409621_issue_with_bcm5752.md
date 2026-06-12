---
title: "issue with bcm5752"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by Treebeard on 2007-04-14
Hello all,

Today I installed Ubuntu 6.10 on my new laptop (Dell Latitude D820). 
The Ubuntu install was succesfull, but I still have some issues with my (wired) NIC.
After a few hours of debugging and googling, I'm not sure where to look further.

In the box I have a Broadcom NetXtreme BCM5752 Gigabit Ethernet NIC.
This NIC uses the 'tg3' kernel module.

When I plug the cable directly to my cable modem, then everything works like a charm.
However when I connect a simple 5-port router to my cable modem and plug  my cable into the router, then the network connection doesn't work properly anymore.
It does work normally when I boot Windows..

This is what I know :
- the tg3 kernel module is loaded
- dmesg reports the driver as working at 100 full duplex
- the router is properly configured (ip : 192.168.2.1), set at 100 full duplex, autoneg off
- the laptop does receive a valid IP from the routers' DHCP
- the default gateway on the laptop is set to 192.168.2.1
- I can ping the gateway
- ifconfig reports a lot of errors
- I can ping remote IP addresses
- At first, it does NOT resove domain names properly. However after a few minutes, it can reslove normally.
- Surfing to webpages gives a timeout, also when I use an IP address instead of a domain name
- I can SSH to a server, but after logging in I also get timeouts

I first thought that it had something to do with duplex mismatch, but I have tried using various settings with 'ethtool'. I don't think that this is a DNS issue...

Anyone have an idea what this can be ?

Thanks in advance,
Cheers

---

### Post by Treebeard on 2007-04-15
I also tried to disable ipv6 and to use a different nameserver.
I Without luck.

f I'm connected behind the router, then I get an awfull lot of errors on RX, none on TX :
```

RX packets:2148 errors:321 dropped:0 overruns:0 frame:0

```This seems to me like a driver issue, but everything works when i'm directly connected .. and there are no errors then... !?

---

### Post by Treebeard on 2007-04-15
Alright, I found a solution...
For some reason the MTU of the interface is set to 1320. Because of this a lot of frames gets dropped. Everything works when I change it to 1500

Manually : 
```
# ifconfig eth0 mtu 1500
```Automatically :
```

in /etc/network/interfaces I use the post-up option to set the MTU (see 'man interfaces'):
auto eth0
iface eth0 inet dhcp
 ** post-up /sbin/ifconfig et0 mtu 1500**

```This is not the most elegant way to set the mtu when using DHCP, but it works :)

---

### Post by RyanGT on 2007-04-16
Do you have your wireless working well on the latitude 820?  Mine hangs at boot for a while and then works o.k. after I log in and restart the networking.  Would you mind posting your /etc/network/interfaces file.

Thanks,

Ryan

---

### Post by Treebeard on 2007-04-22
> **RyanGT said:**
> Do you have your wireless working well on the latitude 820?  Mine hangs at boot for a while and then works o.k. after I log in and restart the networking.  Would you mind posting your /etc/network/interfaces file.

Thanks,

Ryan
I didn't have time to configure wireless yet, since I only have a wireless network at work.
I'll post it here when I've configure it..

Cheers

---

