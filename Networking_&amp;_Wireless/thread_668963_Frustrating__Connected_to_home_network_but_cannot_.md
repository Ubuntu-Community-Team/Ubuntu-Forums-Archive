---
title: "Frustrating:  Connected to home network but cannot use Firefox to browse web, etc"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by udstuen on 2008-01-16
I'm new to Ubuntu still, so you're going to have to baby me through this in plain English.
My ubuntu 7.10 recognizes my home network, but I CANNOT browse the web or use Pidgin.  It seems as if the network has full strength but I can't use the Internet.

What should I do?

At my college this morning (I commute) I noticed that I couldnt connect the the VPN.  So I when I came home I went to the synaptic and searched for openvpn and downloaded/installed everything related.  All the related packages were installed and then I left the house.  When I came home earlier, I attempted to connect to Pidgin and it would not do so, so I deleted all of the related OPENVPN things that I just installed and rebooted the computer.

Now nothing internet related works except recognizing my network and saying that I am connected.

Everything was just fine yesterday and this morning.  I just upgraded from windows XP to Ubuntu 7.10 on a dell e1505.  Even after installing Ubuntu, it recognized my network and immediately asked for my WEP code.  After entering I was able to browse and chat like normal.


This is very frustrating and I need my laptop for other things.  Currently I am on someone elses computer.

---

### Post by wieman01 on 2008-01-16
What does this yield (terminal):
> route
> sudo /etc/init.d/networking restart
You might have to disable IPV6... Look into that matter later on.

---

