---
title: "Wireless SSID priority"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by lamborghiniwang on 2007-10-16
I am running Gutsy on my Thinkpad T61p with the Intel 4965AGN wireless card. The card itself works well, but I am having problem to set priority for the SSID.

I have both wired and wireless connection at home, and the network-manager can automatically switch between wireless and wired connection depends on whether a ethernet cable is pluged in. 
However, things in my school is a bit complicated. We have the a large campus-wide wireless coverage (let's call it wireless-A, WPA enterprise) and a department-wide coverage (wireless-B, different SSID, WPA-PSK). The thing is that wireless-A covers more area but most of the time the signal is weak and speed is not fast. So I would like to know if there is a  way to set a priority for the SSID. Say tell Network-Manger to connect to wireless-B if both signals are available, and connect to wireless-A when it is the only signal available. Right now, Network-Manager kinda picks the AP randomly when both signal appears, and sometime when I ask Network-Manager to switch to another AP, it will stop responding and the wireless card will disappear in "ifconfig" and it can only be solved by a reboot, which is annoying.

I know in windows there is some software in which I can set the priority for both the wireless and wired connections, but I couldn't find something similar in Gutsy. :confused:

Any suggestions?

---

