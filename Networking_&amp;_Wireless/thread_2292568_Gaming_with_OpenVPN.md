---
title: "Gaming with OpenVPN"
date: 2015-08-29
forum: Networking &amp; Wireless
---

### Post by trololo5 on 2015-08-29
Hi,

After years of indecisiveness, not long after upgrading to Windows 10 I finally decided to ditch Windows as my main OS on my gaming computer. Most of my Linux experience comes from RHEL and Lubuntu, but this time I got Mint 17.2 because I just love the Cinnamon desktop. Shouldn't make too much of a difference in this purpose though.
I feel that perspectives for Linux gaming look a lot better than they used to back the first and last time I tried this in late 2012 or early 13. There's just this one thing:
For years I've been playing various games with friends (one guy likes to experiment, rest is Windows guys with 7 or even Vista) through Hamachi and, after Hamachi started pissing us off too much, Evolve - some HoMM, some Civ, some other stuff, but in particular we played the crap out of Empires: Dawn of the Modern World [SIZE=1](sadly pretty much a dead game, and has a garbage rating in WineHQ from 2009...)[/SIZE] and later Minecraft. Now, the game runs perfectly natively and so does the server BUT of course the only way for me to play MInecraft while on my gaming PC with Linux and with my friends is by running the server on my laptop with Windows and Evolve.

It didn't take me long to google that the messianic application to solve this connectivity problem would be OpenVPN **and** there are even instructions on how to set it up... but 90% of it is gibberish to me. I've taken a network class for a year but so far we haven't done much more than about the functions of some devices, half of which are obsolete, topologies and cable types. :D I know what a DNS is for and how to set up eth0 with a static 10 or 192 IP [SIZE=1](but only if it's under /etc/sysconfig/network-scripts)[/SIZE], and that is where my networking knowledge pretty much ends already. So I have no idea what I am doing... yet.


Anyone here who ever set up something like this and actually understands?

Edit: Okay, buy just following instructions such as [https://openvpn.net/index.php/open-source/documentation/howto.html](https://openvpn.net/index.php/open-source/documentation/howto.html) and [https://www.howtoforge.com/internet-and-lan-over-vpn-using-openvpn-linux-server-windows-linux-clients-works-for-gaming-and-through-firewalls](https://www.howtoforge.com/internet-and-lan-over-vpn-using-openvpn-linux-server-windows-linux-clients-works-for-gaming-and-through-firewalls), I managed to get the openvpn server installed and without errors on my PC and the client configured on my desktop. But connection fails with no output at all. That makes it hard to figure out. Maybe it's because I configured all the client certificates centrally and just moved one set over with an USB Stick?

---

