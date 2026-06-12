---
title: "ifup and ifdown"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by AndEat on 2007-12-15
This install of K/ubuntu 7.10 I'm getting odd responses from ifup and idown. Right now I have no idea why they are not working 

ifdown eth0
ifdown: interface eth0 not configured

ifup eth0
Ignoring unknown interface eth0=eth0

I get the same result w/sudo and while sudo su'ed

Networking is working, i.e. I have an internet connection, but no idea offhand ifconfig shows eth0 is up and configured.

This is my first post and I am investigating. 

:confused:Any information appreciated.

---

### Post by spd106 on 2007-12-15
As far as I am aware the ifupdown scripts only work with the /etc/network/interfaces file. So if your interface is not defined in there it won't be able to find it.

Instead Network Manager is in control of all network interfaces be default. If you want to use ifupdown I think you have to turn off roaming mode.

---

### Post by AndEat on 2007-12-15
ok, 

I did scan that and uncommented the eth0 entry -- it was from the original setup, at no point did I comment it out. 

I do remember reading something on the forums here about the network manager being implicated in issues like this but I'm fuzzy about the exact details. Here is firsthand experience for me.


thanks

---

