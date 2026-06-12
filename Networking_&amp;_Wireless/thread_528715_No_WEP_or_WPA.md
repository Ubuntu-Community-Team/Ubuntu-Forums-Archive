---
title: "No WEP or WPA"
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by Ron Overdrive on 2007-08-18
Sup guys, I'm kinda new but I've been able to trouble shoot most of my problems without asking (search does wonders ;) ). However I've run into a snag with my wifi on my laptop. I'm currently running XUbuntu 7.04 with the 2.6.22-9 kernel with all the wpa stuff installed on my ASUS A7T-X1 laptop. Goto Network settings and configure my access point and wep key, nothing no internet. Tried using WPA on my friend's network, nothing. But I get internet on open networks. I've tried using at least 4 different GUI interfaces and have tried command line settings to see if I can get it to work. Nothing. Tried upgrading the Madwifi drivers, nothing. Tried using Madwifi-ng and still no go. Went back to the normal Madwifi drivers and currently looking for a solution. In all the GUI's they won't allow me to select and switch to a secure network at all. This is kinda disconcerning because we use Wifi alot at work and we really have no Linux guys in the office to help me out with this. Any ideas what I could be missing?

---

### Post by luisromangz on 2007-08-18
I recommend to use WICD, google for it, is the best tool, because it works.

It allows you to define profiles for the wired conection, and manages the wireless card, with both WEP and WPA correctly.

---

### Post by Ron Overdrive on 2007-08-21
Thanks man, got to try it out at work and it works perfectly.

---

