---
title: "How to turn on the wireless card"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by jackychanqn on 2007-06-03
I a using HP nx6120 now. It has a button to turn on the wireless card, but now I can´t use it. But I have installed the wireless card in ubuntu. Please help me !

---

### Post by elquer on 2007-06-04
i have a compaq ( made by hp) and having the same problem, what version is ur chip set, processor type and let me know whether ur running a 64 bit version of ubuntu. i was able to solve this problem while using 6.06 but not in 7.04.

---

### Post by kevdog on 2007-06-04
Im going to take a stab in the dark at this one

Assuming you used ndiswrapper to install the wireless card, try the following:

sudo iwconfig wlan0 essid on

Again assuming the wireless interface is wlan0 (maybe eth0), essid (try substituting essid name of your LAN)

If nothing happens try:

sudo iwpriv wlan0 ndis_reset

Just a thought

---

### Post by kevdog on 2007-06-04
Another link you might want to check out (never done this so I cant say):

[http://rfswitch.sourceforge.net](http://rfswitch.sourceforge.net)

---

