---
title: "Internet slow/non existant"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by Origin415 on 2007-02-09
I have recently installed Ubuntu 6.10 and the only problem I seem to have is with my network connection.

My network card is my onboard nForce2 ethernet card, and I am on a college campus network behind their firewalls and the such.

It ranges from essentially disconnected to rather normal, but it is far more common to be the former.

I have yet to successfully ping any site, whether I use the ip address or domain name, running host [www.google.com](www.google.com) is usually pretty slow, and mostly just times out. Browsing the web with Firefox is arduous at best.

This said, I have searched the web for solutions, and the only one I could find which sounded like it could fix my problem was disabling ipv6, which I attempted to do in every variation I found including editing the alias file, adding a bad_list file, and changing it in about:config in Firefox, but have been unsuccessful, ip a | grep inet6 still outputs information.

Any help on disabling ipv6 or fixing whatever else it could be would be awesome.

Thank you in advance.

---

### Post by lavinog on 2007-02-10
did it work before you installed ubuntu?
Have you tried to ping or access your college's website.

My college blocks all pings with their firewall as a security measure.

Also at my college everyone complains about how slow it is, but I'm willing to bet that majority of the problems are because everyone on campus is using p2p programs.

being that you said that you can connect to google, you may want to get help from your campuses IT department...It could be the network and not your computer.

---

