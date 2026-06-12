---
title: "Wireless-to-wireless internet sharing?"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by bas1 on 2008-05-10
Hi all,
What I want to do is to share a wireless internet connection between my laptop and my iPod touch so I can have a second network for my iPod touch (even though my laptop can get signal, my iPod can't). I've done wired-to-wired before, but not wireless-to-wireless. My hardware setup is below:

**eth1 (built-in wireless card w/internet)**

ip: 192.168.1.202
netmask: 255.255.255.0
gateway (my router): 192.168.1.1

**wlan0 (wireless PCI adapter to be connected to iPod)**
ip: 192.168.0.1
netmask: (?)
gateway: (?)

And here is another way to look at it:

Router >> my laptop >> iPod Touch

P.S. I have looked at [this how-to]("http://ubuntuforums.org/showthread.php?t=91370"), but it doesn't cover the part where I need to make another wireless network.

---

### Post by bas1 on 2008-05-12
<Bump>

---

