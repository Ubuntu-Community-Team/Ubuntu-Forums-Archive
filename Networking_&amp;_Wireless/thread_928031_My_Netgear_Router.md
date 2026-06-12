---
title: "My Netgear Router"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by new@this on 2008-09-23
I have Ubuntu installed and working fine on a Dell laptop.  I can connect to my home network with an ethernet cable plugged into my laptop, but not wirelessly.  I can connect wirelessly to other newtworks though.  Is there a known issue with older Netgear wireless routers?

---

### Post by howefield on 2008-09-23
Which model are you using ? I am using netgear which works well, DG834GT with the supplied wireless adapter WG111T

---

### Post by willca on 2008-09-24
How does your netgear router expect you to connect to it?
WEP, WPA, or no encryption?

Does your wifi nic see it at all?
sudo iwlist wlan0 scan

Could there be other wireless routers in the vicinity that uses the same channel and has better signal strength reception than yours?

---

### Post by lisati on 2008-09-24
I use a WGR614v7 from Netgear, no major hassles. Perhaps updating the firmware when hooked up by cable is an option.

---

