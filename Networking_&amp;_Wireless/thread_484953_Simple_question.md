---
title: "Simple question"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by U2XS on 2007-06-26
I have a password protected (Win XP) wireless network.  I installed Ubuntu on another computer and it connects to *a*  network, but since I see it doesn't ask for a password, it can't be *my* network.  How do I change the router that Ubuntu connects to?

In windows, there is a list of available routers in the area.  Is there a comparable list in Ubuntu?

---

### Post by kevdog on 2007-06-26
First determine your wireless interface name:

ifconfig

Its probably either eth0, eth1, wlan0

Then
iwlist *interace_name* scanning

This should show you the networks in your area.

---

### Post by speaker219 on 2007-06-26
If you don't know your interface name, just type:
sudo iwlist scanning

---

