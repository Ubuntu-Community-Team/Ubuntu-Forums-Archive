---
title: "I would like to share my internet connection."
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by wilsonsamm on 2008-06-27
G'day maties,
I have here my Ubuntu box, with two ethernet cards. eth0 is connected to the internet, and I would like to be able to hook my laptop up to the internet through eth1.

I have been looking at this document:
[http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.5.html](http://en.tldp.org/HOWTO/IP-Masquerade-HOWTO/ipmasq-background2.5.html)
which seems to explain how to do it, except that I don't have a static IP (I'm happy to use DHCP to find a new IP every time), and I'd also like a DHCP server to give any computer on my eth1 an appropriate IPm so that friends who bring their computers 'round don't need to configure their connection to use a gateway every time.

Do I correctly understand the role of a DHCP server?
If so, how can set this up?

---

### Post by Iowan on 2008-06-27
[Here ]("https://help.ubuntu.com/7.10/server/C/dhcp.html")is some DHCP info.  Sounds like you have the right idea. You'll probably want a static address for eth1, a DHCP server can be set to use that for clients.

---

