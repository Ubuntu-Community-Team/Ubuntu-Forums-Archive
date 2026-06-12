---
title: "Ad-hoc wifi connection between PC and Phone"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by foufoutos on 2007-06-17
Hello everybody,
I am doing my MSc thesis project and I need to connect my phone with my Pc over a wifi ad-hoc connection.

My pc has two interfaces, eth0 (a wired interface connected to the internet) and eth1(the WiFi interface).

I have been able to set the eth1 interface to ad-hoc mode using this

sudo iwconfig eth1 essid "MyPc" mode Ad-Hoc channel 2

command. I am trying to assign it an ip address using dhclient but it fails to do so. Anyone has any idea what the problem might be?

As a followup question I would like to know how is then possible for my Phone to share the wired interent connection of eth0 over the wifi interface eth1...

Any ideas are appreciated.

---

