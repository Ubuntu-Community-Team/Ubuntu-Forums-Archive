---
title: "One Wired and One Wireless Connection"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by infecticide on 2008-03-06
Here is my setup:

1 Wireless R8187, works fine when KNetworkManager takes care of it from the default install.    192.168.x.x/24

2 Onboard Gigabit ethernet ports, I use one as a dedicated line to my server.    10.x.x.x/8

It seems like KNetworkManager is meant to allow only one interface to be active at a time.  Is this the case?

I tried to use KNetworkManager to setup a manual configuration for these two interfaces but after I do that all network connectivity is toast and KNetworkManager is useless for configuring anything else.


Any idea how I setup static addresses for both these interfaces?  I cannot assign static addresses from the Router because Linksys didn't include that feature in the firmware on this model.

Bonus points if I can still use KNetworkManager to manage my wireless.

Thanks in advance.

---

### Post by wieman01 on 2008-03-06
First of all, yes, (K)NM can handly only one connection at a time, plus... you'll find that very annoying... it cannot handle static IP addresses (yet).

Now to remedy this shortcoming (static IPs) you can either install [WICD]("http://wicd.sourceforge.net/") for wireless networking or follow my WPA tutorial (signature) which will explain to you how to do it manually through a terminal. But I don't recommend it if you need 2 connections at a time.

The next version of Ubuntu (Hardy) will ship with a version of NM that supports static IP addresses as far as I know.

---

