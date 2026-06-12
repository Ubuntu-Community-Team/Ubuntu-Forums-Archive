---
title: "Hidden college SSID, ubuntu 8.04 woes"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by (-NINJ4-) on 2008-09-04
I've got a Linksys wireless PCI card in my desktop (Broadcom BCM4306, fwcutter drivers installed and updated as of today) because my dorm this year does not have ethernet wiring.  However, it does have wireless.
Unfortunately, the wireless network's SSID is hidden and has a WEP encryption key.  After futzing with the default network manager I found no relief, and then proceeded to seek these forums from beginning to end, and found out there's supposedly an ongoing(?) issue with ubuntu connections with hidden SSID networks, so I installed wifi-radar, which also failed to connect to the network.  I'm wondering if there's any hope to be had for connecting to a passworded, hidden SSID network in Ubuntu 8.04?

Unfortunately this isn't a situation I can remedy by making the SSID visible (since it's the college's network) or by using a solely wired connection on the desktop (building isn't wired).

My Windows XP laptop and iPod Touch both connect to the hidden network without issue.


Thanks in advance for any help you can give,
M

---

### Post by arm-c on 2008-09-05
My wife is having same problem at her university where she can't see / connect to the network.  Has tried manual connection.

She is 8.04 with latest updates from main repositories.

HELP!!!

---

### Post by HermanAB on 2008-09-05
Make a little script and feed the parameters to the thing, then put a link on the desktop.  Read the ifconfig and iwconfig man pages and google a bit for an example.

Cheers,

Herman

---

