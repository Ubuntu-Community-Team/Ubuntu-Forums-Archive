---
title: "Share Ethernet to Wireless"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by bloodniece on 2006-09-07
I use my Dapper 6.06 box as a desktop connected to my LAN via ethernet.  I want to  use my Dapper box as a wireless access point for mobile users in my office.
So, I need to share eth0 *(Gigabit ethernet nic)* with eth1 *(Linksys card, working)*.  Are there any solutions for this?  

I have a 24" D-Link omni 6db antenna connected to it so I'm sure it will be a nice strong signal.  I don't want to mess with DHCP, I just want to create a network with my wireless NIC that uses my ethernet NIC as a gateway.  My W2k box handles DHCP.


Cheers

---

### Post by tbonius on 2006-09-07
A quick Google of "Linux Wireless Access Point" spit back quite a few results:

[http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html](http://oob.freeshell.org/nzwireless/LWAP-HOWTO.html)

[http://www.enterprisenetworkingplanet.com/nethub/article.php/3463611](http://www.enterprisenetworkingplanet.com/nethub/article.php/3463611)

I havent personally tried it with Linux.. only FreeBSD.. but thanks for the idea.. I will build one tonight and post an article:

-Shameless Plug:-

[http://www.section6.net/wiki/index.php/Main_Page](http://www.section6.net/wiki/index.php/Main_Page)

Tutorials for Linux and BSD

T

---

### Post by bloodniece on 2006-09-08
Thanks, I'll try it out. I know it is easier to just go by a WRT54 and throw openwrt on it and call it a day, but.....I like a challenge. :p

---

