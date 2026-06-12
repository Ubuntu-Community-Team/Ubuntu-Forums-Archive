---
title: "No Ethernet connection on Lubuntu 14.04"
date: 2014-09-12
forum: Networking &amp; Wireless
---

### Post by Mentalhead on 2014-09-12
I'm using Lubuntu 14.04 on my old PC, but it seems that my Ethernet connection isn't working.
I have two computers connected to my router, one runs W7 and other one runs Lubuntu. 

As for router, it's working correctly, it worked with Windows for years.

In order to get Ethernet connection working on Lubuntu I need to unplug Ethernet cable that goes to my computer that runs W7 and plug it back in, and everything starts working as it should on Lubuntu.
I tried starting Lubuntu from USB Flash Drive, and the same problem occurs.

Can somebody explain to me what's the problem here? 
Bear in mind that this is my first Linux distro, so try to keep your answers simple.

---

### Post by varunendra on 2014-09-12
Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands :
```
sudo lshw -C network
ifconfig
egrep -im20 'dhcp|dhclient' /var/log/syslog
```
You can copy-paste the above commands from here to the terminal using your mouse cursor to avoid typo.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Mentalhead on 2014-09-13
It appears that I have fixed the issue. Since my computer is old I had to set Link Duplex to 10Mpbs instead of 100Mbps.
However, I didn't know that I left auto-negotiation on, and this was the problem.

After setting auto-negotiation to off via ethtool everything seems to be working without problems so far.

---

### Post by varunendra on 2014-09-13
Congrats, and thanks for the feedback!

Please mark the thread as [SOLVED] using "Thread Tools" link above the first post.

---

