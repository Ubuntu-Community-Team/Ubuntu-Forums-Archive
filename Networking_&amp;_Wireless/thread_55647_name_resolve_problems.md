---
title: "name resolve problems"
date: 2005-08-09
forum: Networking &amp; Wireless
---

### Post by Copter on 2005-08-09
hi!

i have this strange network problem. when system starts it fails while setting clock from some ubuntu adress. when kde is loaded i dont have internet connection. im connected to inet through server. i can ping it (10.0.0.1) but cant ping anything else.

i ran KNetworkConf from kde menu -> controll center -> network settings (or something like that - posting from windos :-x). i saw there that my gateway adress is not set (10.0.0.1 - i set it on kubuntu install). i tried to change it but it doesnt want to save it. when i run this app again i see that gateway is not set again.

the strangest thing is that after using this network app i see cpu usage increase to 100% (other apps not running, cpu = celeron 2.6GHz). when running top i see that almost whole cpu is stolen by perl. i know only one app on my system that uses perl and its frozen-bubbles :). before using this network config tool perl wasnt running (or maybe it was asleap, dont know).

what is going on?

copter :]

EDIT: i used route add default gw 10.0.0.1 and it worked. still dont know why this config tool stoles my cpu using perl...

---

### Post by WoodyDragon on 2005-12-06
[http://bugzilla.ubuntu.com/show_bug.cgi?id=9871](http://bugzilla.ubuntu.com/show_bug.cgi?id=9871)

The bug seems rather old, but I stumbled over it with breezy on my notebook (2 interfaces)... 
Luckily I know how to set routes. The best solution is to edit /etc/network/interfaces by hand and not to use knetworkconf for the time being.
For a newbie to linux such an experience can be very frustrating as the network seems "not to work at all".
This should not be too hard to fix. :???:

---

