---
title: "(k)networkmanager works only with dhcp?"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by hardhu on 2006-10-27
I was looking for a network switching tool easy to use for my laptop running kubuntu edgy, and, following some suggestions found in this forum, I have decided to give (k)networkmanager a try. So I installed network-manager and knetworkmanager packages, and I tried to see it it would really make "linux networking easy". In my case, this isn't really happening :( ; let's consider only the wired connection, to keep things simple. As long I have dhcp enabled in my dsl router (what I don't want), everything is fine, (k)networkmanager connects to it and gets the address, but I could get the same result with a single line in /etc/network/interfaces...
But if I disable dhcp, then (k)networkmanager gets stuck,, it tries to connect to the router for a while, and after that it brings up eth0 with ip address 169.254.141.132, that really does not make sense in my case, since the ip address of my router is 192.168.1.1  :confused: 
I would like to have 192.168.1.3 as ip address of my ethernet card, but I couldn't find any way to obtain it through (k)networkmanager.

So what?
Am I doing something wrong?
Is (k)networkmanager supposed to work only with dhcp?
Is this a only kde-related issue and in Gnome everything works?

---

