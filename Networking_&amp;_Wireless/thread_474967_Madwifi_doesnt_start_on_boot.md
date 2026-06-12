---
title: "Madwifi doesnt start on boot"
date: 2007-06-15
forum: Networking &amp; Wireless
---

### Post by heroinhero on 2007-06-15
For some reason, madwifi refuses to pick up an IP address on boot. On boot, the status with the AP is 'not associated' (when using iwconfig ath0). Yet it does show the correct ssid.

It usually doesnt even work when I do dhclient ath0 either.  First i need to do ifconfig ath0 down, then ifconfig ath0 up, and then dhclient for it to finally work.

Anyone have any suggestions?

---

### Post by growler on 2007-06-16
I have the same problem after upgrade to 2.6.20-16-generic... fixed by 

sudo /etc/init.d/networking restart


growler

---

