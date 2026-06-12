---
title: "Iptables"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by Jawshie on 2008-03-22
I followed this guide to set up a wireless network from my desktop:
[http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html](http://anojrs.blogspot.com/2007/07/ubuntu-creating-wireless-home-network.html)

Now I am done with it and I want to reverse what I have done with IPTables and such. Can anybody guide me through this? I am connected using the same wireless card to a different wireless network so it shouldn't be broadcasting anymore.

---

### Post by anojrs on 2008-03-23
Hi Jawshie

To clear all the rules in your iptables :
$ sudo iptables -F

To revert back, (clear ip_forward)
comment the "net.ipv4.ip_forward = 1" in /etc/sysctl.conf

(stop ipmasq  service)
$ /etc/init.d/ipmasq stop




Regards
Anoj
[http://anojrs.blogspot.com](http://anojrs.blogspot.com)

---

