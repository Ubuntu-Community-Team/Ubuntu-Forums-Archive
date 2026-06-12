---
title: "Intel Pro/Wireless 2200BG: Frequent wireless disconnection"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by wjbmd48 on 2015-02-08
Hi:

I'm running a Thinkpad X40 on Lubuntu 14.04.1; my wireless adapter is PRO/Wireless 2200BG [Calexico2].

I find that I'm getting kicked off frequently from my network, which runs a maximally complex 63-character WPA2-TKIP code, which I need in a crowded building.

Most of the time simply clicking on the connection, recycling the settings, doing a sudo service network-manager restart works; in a worst case scenario, I have to reboot.

A minor annoyance I've learned to live with, but any ideas? Is there a simple script I can run that will automatically reconnect me when this happens?

Thanks,

Bill

---

### Post by chili555 on 2015-02-08
First of all, I highly recommend AES instead of TKIP. TKIP is less secure. Second, as you know, your oldie but goodie Intel 2200 doesn't do 802.11N. I suggest you try changing the router to B and G only instead of B, G and N. I'd also try turning off power management at the driver if it's on:```
iwconfig
```If it says Power Management: on, then try:```
sudo iwconfig eth1 power off
```I believe the wireless interface for this driver is eth1, not the conventional wlan0; adjust as needed.

If this helps, we can make it persistent.

---

### Post by wjbmd48 on 2015-02-08
Thanks! I'll try all that, report back.

Greatly appreciated! You guys are the best!

Bill

---

### Post by wjbmd48 on 2015-02-09
Hi:

Thanks!  Changing to AES, switching routers, and making the broadcast g only seems to have done the trick.

Bill

---

### Post by chili555 on 2015-02-09
Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by wjbmd48 on 2015-02-09
Done, thanks again!

Bill

---

