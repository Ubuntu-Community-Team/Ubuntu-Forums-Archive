---
title: "Getting message: Disconnected"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by cyndyleavitt on 2008-11-30
I've tried several different configurations but always end with the same message: "Disconnected, the network connection has been disconnected."  I have a cable connection and the computer is connected directly through a wire from the router.  I understand it is difficult to connect using Ubuntu and a router but I also have a wireless and that doesn't work either.  Can someone please point me in the right direction.

I have been working with Ubuntu on a PC in order to learn Ubuntu.  My new business has an Ubuntu Server and I need to learn as much as possible.

Thanks for any help you can be.

---

### Post by gpsmikey on 2008-11-30
What router are you using ?  Do you have any other machines on the network that your Ubuntu machine can talk to ??  I have a Linksys WRT54G (connected to Comcast) that seems to have no issues.  I did put "Tomato" on the router a while back (replacing the Linksys firmware), but have not experienced any issues.  There are a number of machines on my LAN (mostly windows) with 1 Ubuntu file server (static IP) and another one just for playing (8.10 desktop) around that uses DHCP to get an address.  Have not seen an issue with either for weeks.  There have been several people report issues connecting, but I have not seen any.  The trick here is to see if the connection fails when you are connected to the outside only, or when you are connected to anywhere in the LAN (if no other machines in your network, try logging into your router and snoop around it's web pages - see if you get disconnected from there).  If none of that helps, let us know what router you are using, what version of Ubuntu you are using etc and hopefully someone will have some clever ideas.

mikey

---

### Post by superprash2003 on 2008-12-01
post output of ifconfig from the terminal .. what is your router ip address?

---

