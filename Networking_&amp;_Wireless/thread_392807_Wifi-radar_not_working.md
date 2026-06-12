---
title: "Wifi-radar not working"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by weijie90 on 2007-03-24
Hi,

When I click on the "edit" button in wifi-radar, after selecting my AP, nothing happens. How should I use wifi-radar? 

Thanks!


//EDIT: Solved! Comment out lines not containing "lo" in /etc/network/interfaces .  The panel applet works now.

---

### Post by elcasey on 2007-03-25
Wifi Radar is not an application used to configure wireless cards or to connect to wireless APs. It's merely a scanner for detecting WAPs.

Unless you have a Ralink card, try to select your AP via the Networking applet in your "system tray" or in System=>Administration. You can select or specify your WAP there. If you have a Ralink PCI card (like I do), search the forums for a howto on installing the driver for that...because if you use Networking, it will lock up your entire system.

---

### Post by weijie90 on 2007-03-25
Hi,

I searched around for a nm-applet solution and found out that I had to comment out all the lines not containing "lo" in /etc/network/interfaces. 

Thanks!

---

