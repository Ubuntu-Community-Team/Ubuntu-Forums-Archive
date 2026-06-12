---
title: "Can't Find Network"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Mrhankymk on 2007-07-10
Hey,

I just installed Ubuntu successfully and am amazed by its speed compared to my current XP. So in turn I want to start using it every day (programming, watching videos, etc.). The only problem is I can't without the Internet.
I looked into my network connections (that's what it's called in Windows.. Forgot what it is in Ubuntu but you know what I mean hopefully) and I saw something about 2wire which I remember seeing before in Windows although I don't see it when I switch over to Windows (dual boot). Although on the Linux machine I can't see the network I need to connect to. I don't want to advertise the SSID so we'll be calling it Fred . The network is verified via mac address so in the Windows driver of my networking card (a Blitzz Super G wireless PCI card) you see a network with a blank SSID but in Linux I see nothing of it so I am assuming I can't see it in Linux because I need to be authenticated. Although my mac address should stay the same on both OS's. If I lost you I'm sorry. I've pretty much lost where I am in the story myself. But bottom line does this mean my card isn't recognized my Linux and I need to use a program to use my current Windows driver? Or does this just mean I need to change my hostname or something so the router can recognize me?

---

### Post by spd106 on 2007-07-10
Network Manager 0.6.4 seems to have trouble connecting to non-broadcasting wireless networks. So you will either have to wait for the next release, turn broadcast on, use a different utility or perhaps use wpa_supplicant by editing text files manually.

There are multiple guide to doing both of the last two options around this forum.

---

