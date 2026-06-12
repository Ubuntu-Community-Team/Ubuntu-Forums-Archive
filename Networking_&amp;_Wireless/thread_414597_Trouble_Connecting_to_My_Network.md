---
title: "Trouble Connecting to My Network"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by JoshEngleman on 2007-04-20
Well, after a few years of debating it, I finally bit the bullet and decided to check out a Linux distro. I installed Feisty today and didn't really have any major problems. I wasn't able to connect to the wireless network initially. I booted into XP to search for some work arounds and saw that using Wicd might help. I installed Wicd but I still couldn't connect. I was able to connect to my neighbors unsecure network, but not to my WEP network. Also, I am barely showing any signal strength for my network, and my neighbors is on the low side too. I have a Belkin FD57000 wireless card, if that matters.

Any help would be great.

---

### Post by j0sh0 on 2007-04-20
you need to know the SSID of your router, is the network open or shared, the encryption key, and the channel (or frequency) the router is broadcasting on. once you know all this, go to a terminal and type:

sudo iwconfig {interface} essid {SSID of router} channel {channel} key {WEP key}

let us know if this helps

---

