---
title: "wlan0 connection pops up every few hours!?"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by ranbo on 2008-03-24
Whenever I bring my wired "eth0" connection up, several hours later it stops working, and when I do "ifconfig", I see that "wlan0" has come up, too! What is doing that??

The "Network Manager" in ubuntu seemed cool at first but gave me so much grief that I eventually uninstalled it from my machine and wrote scripts to bring wireless and wired connections up and down.  I can use those to reliably get wired and wireless connections.

However, the mystery is that after running "sudo ifup eth0" to get a wired connection, a few hours later it stops working and I have BOTH "eth0" and "wlan0" listed.  I don't know what process is causing that to happen.

When I bring the wired connection up, it says:

  There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
  ...
  DHCPREQUEST on eth0 to 255.255.255.255 port 67
  DHCPACK from 10.52.38.1
  bound to 10.52.38.107 -- renewal in 8778 seconds.

First of all, I'm not sure why there's a renewal in 8778 seconds.  That appears to be about how long my connection stays active before getting auto-hosed.

Secondly, I'm not sure why wlan0 would automatically come up after that point.

Any ideas?

---

