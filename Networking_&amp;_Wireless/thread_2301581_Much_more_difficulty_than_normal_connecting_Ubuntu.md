---
title: "Much more difficulty than normal connecting Ubuntu 14.04.3 server to WPA2 network"
date: 2015-11-03
forum: Networking &amp; Wireless
---

### Post by austin_brown on 2015-11-03
I am having a *lot* of difficulty connecting ubuntu server (14.04.3) to my wireless network. I have already set up my /etc/network/interfaces correct (if needed, I can give the details for it), and I've set up /etc/wpa_supplicant.conf. Any time I do ```
sudo ifdown wlan0 && sudo ifup -v wlan0
``` I get different errors each time. Also when i run ```
sudo wpa_supplicant -B -D wext -i wlan0 -c /etc/wpa_supplicant.conf
``` or whatever it is, it is something along those lines (got up almost half an hour ago, brain not working at full potential) I also get errors. I am looking for a way to solve this, and I do have access to a wired network that *does* work if needed. Please help me with this, as I have installed Ubuntu Server on my old laptop, and i plan to use it for many different "things" ;) Once again, Thanks a ton in advance.

---

### Post by SeijiSensei on 2015-11-03
I'd just stick with a wired connection for a server especially if you expect it to be running 24/7.  Plus you'll get better network speeds over a wire; even 100Mbit Ethernet is faster than most wifi connections, and none of those can touch Gigabit Ethernet speeds.

---

