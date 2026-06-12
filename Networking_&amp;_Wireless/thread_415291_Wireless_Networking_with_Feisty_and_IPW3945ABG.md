---
title: "Wireless Networking with Feisty and IPW3945ABG"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Tuxedo Mask on 2007-04-20
Greetings,

So I installed Feisty overnight, and for the most part, I've not had any problems.  I noticed that NetworkManager automatically connected and recognized the driver for my Intel PRO/Wireless 3945ABG card, always a plus.  I unplugged my wired connection and the program tried to find a wireless network - YAY!  Connected - excellent.  Firefox - hmm.  The page takes forever to load, and when it does, I get an error.  Foo, I reply, and try ping -c 4 [www.google.com](www.google.com).  Unknown host.

-_-

I'm not sure where, exactly, the problem is.  ifconfig and iwconfig both show eth1 enabled and connected to the network.  ifconfig does show that there are 8 (!) errors, but I don't know how to read the log to find them out.

Can anyone help my situation?  I'll provide more info if needed.

---

### Post by chili555 on 2007-04-21
I suspect you have a DNS issue. DNS nameservers translate names to numbers; such as, [www.google.com](www.google.com) to 64.233.161.147. You might try *ping -c3 64.233.161.147* If you get ping returns, then you know you are connected but not resolving names correctly. 

When you connect with DHCP, your router, modem, etc. is supposed to offer DNS nameserver IP addresses to populate your /etc/resolv.conf file. Sometimes things don't go as planned in this imperfect world. You might try:```
sudo ifdown eth1
sudo dhclient eth1
``` and see if your /etc/resolv.conf was corrected. Check with *ping -c3 [www.google.com](www.google.com)*

Firefox taking forever is often an IPv6 issue: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

