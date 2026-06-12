---
title: "Wireless in changing locations"
date: 2014-07-03
forum: Networking &amp; Wireless
---

### Post by paljenczy on 2014-07-03
Hi,

I have the following problem: when I'm arriving at my workplace and I have used my wifi at home, although my system sees and connects to the workplace wireless, there is no connection (tested with ping). I can fix this by typing

sudo bash
dhclient -r
dhclient wlan0

However, when I'm arriving home, I have to do the same to get the wifi working. Same applies to any other places when I'm trying to connect to a new wireless system.

My system is Ubuntu 12.04LTS, using a Lenovo Thinkpad X230, Wifi: Intel Corporation Centrino Wireless-N 2200

Could you please help me how to fix this? Typing the commands above are really annoying.

---

### Post by ajgreeny on 2014-07-03
Is one site using dhcp and the other static IPs?

---

### Post by paljenczy on 2014-07-03
I'm not sure - where could I get info about it? Strange thing is that for around half a year, there was no problem at all. Once then, the problem started to appear and it never went away.

---

### Post by fyfe54 on 2014-07-04
Sounds like somebody changed something and didn't think it important to share.

---

