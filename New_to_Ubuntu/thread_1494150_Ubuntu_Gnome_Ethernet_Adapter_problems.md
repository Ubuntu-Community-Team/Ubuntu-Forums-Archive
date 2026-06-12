---
title: "Ubuntu Gnome Ethernet Adapter problems"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by yousamook on 2010-05-26
hey guys,
 
First post, I decided to install Ubuntu 10.04 LTS on my laptop using Wubi. It installed fine and seem to have installed the drivers as well. The issue is that I cannot get online, the network connection Icon has a red exclamation mark and says No Network Connection. If I right Click on the icon it has Enabled for Networking, Wireless and Notifications. If I left click on it, it states Wired Connection "disconnected" Wireless Connection "disconnected". I have the ethernet cable plugged in so it should be connected. 
 
I went to the Terminal and did an ifconfig -a. eth0 and wlan0 come up but do not have an inet IP address. I tried to manually type on in to eth0 and tried to do a down and up. Verified that the IP was set, tried to ping and said network unreachable. if I swtch over the the XP version the internet works just fine. I did an lspci and the two adapters do seem to come up there. I am working with a Dell Latitude D510 laptop. Its old, but it still runs. Any Ideas or suggestions would be greatly appreciated.

---

### Post by zvacet on 2010-05-28
Did you tried t o configure network under **wired** or **wireless**?

---

### Post by yousamook on 2010-05-28
> **zvacet said:**
> Did you tried t o configure network under **wired** or **wireless**?


Both wired and wireless, i was reading up on a driver for the wireless called ipw2200 but that did not seem to work. with the wired connected i tried to set a static IP from the router but still nothing, I took the laptop to school and tried to connect to that network which I know for a fact people running ubuntu can connect but mines still did not connect. When i did a #lscpi command i see the broadcom info there for the ethernet adapter on the wired and wireless but nothing. Not sure if those arethe drivers it should have though.

---

