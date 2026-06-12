---
title: "Fresh install 16.04 on Lenovo U41, neither Ethernet nor WiFi"
date: 2016-05-19
forum: Networking &amp; Wireless
---

### Post by e_Vie on 2016-05-19
Hi all,

my first post in this forum - in the last years of using Ubuntu, it has been of great help, and I've been able to solve any problems I've had with your posts.
I recently got a Lenovo U41 and installed 16.04, but neither Ethernet nor WiFi are working. Plugging in the network cable results in the WiFi-Symbol looking like it would connect, but not connecting; furthermore, the existence of the cable is recognized, but I can't connect to the Internet. The notebook had OpenSuse installed before, where the connection was working flawlessly.
Since there is no cable connection possible, I can't install any Broadcom (BDM4352 802.11ac,  [14e4:43b1] (rev 03)) drivers - I've tried several things, but I just don't really know where to start. How can I get this thing to work? I'm currently connected on another machine, posting from there.
Please see the wireless-info script output that I have attached. I appreciate any help. Thank you.

---

### Post by vasa1 on 2016-05-19
What happens if you choose "DSL" instead of "ethernet" as your connection type?

---

### Post by e_Vie on 2016-05-19
> **vasa1 said:**
> What happens if you choose "DSL" instead of "ethernet" as your connection type?

Hi vasa1, I tried adding a DSL-connection, but nothing connects - it doesn't even show up in the connections list.
The cable connection is visible in the list but greyed out even though the cable is plugged in.

---

### Post by e_Vie on 2016-05-19
Anyone have an idea? I would appreciate any pointers.

---

### Post by Rick St. George on 2016-05-19
Apparently this is a BUG and we all waiting on a FIX. It has even affected previous versions and flavors since the last update!

---

### Post by e_Vie on 2016-05-19
I was also just starting to read into that -- is this card known to work on 14.04?

---

### Post by e_Vie on 2016-05-20
I now solved my problem, but not in 16.04. I installed 14.04 and followed this guide: [http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r](http://askubuntu.com/questions/590442/how-can-i-install-broadcom-wireless-adapter-bcm4352-802-11ac-pcid-14e443b1-r) 
The Wifi works now, but sadly no solution for 16.04.

---

