---
title: "Connection Problem"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by csall on 2008-02-28
Got mu bcm4318 wireless card up and running. However, I would like to bypass knetwork manager and edit my /etc/network/interfaces file to automatically load my wireless settings. Previously I did something along these lines in this file:

auto wlan0
iface inet dhcp
wireless-essid GRUNDLE
wireless-enc 1234567890

But for some reason i cannot connect this way. I also cannot connect by using these commands either:

sudo iwocnfig wlan0 essid GRUNDLE
sudo iwocnfig wlan0 enc 1234567890

Thanks for help in advance!

---

