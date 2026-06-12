---
title: "Baaaaad Wireless Linksys (please help!)"
date: 2007-07-06
forum: Networking &amp; Wireless
---

### Post by family on 2007-07-06
Alright, so I just installed 7.04 on my friends desktop, and they all love the OS. However, the wireless card that was previously working great on XP is not working. Only wired connection is available.  Where can I see a list of devices/drivers besides Synaptics that can direct me to a place to properly configure the wireless. Sorta like Device Manager on XP?

---

### Post by fredj on 2007-07-06
Open a terminal and type
sudo lshw -class network
Look at the result and try to identify the wireless card. May be shown as wlan0 or eth1. In that block
look for a driver=.. string this will give you the name of the driver that is loaded for your card.
Now click on the network icon in the taskbar and see if you can see any wireless networks. If so, you can
try to connect to yours. You may need to enter a wep or wpa key. If there are still problems post the 
output from the lshw command here. Also post the contents of your /etc/network interfaces file here.

---

### Post by family on 2007-07-06
Yes, the command worked to a degree, but it asked for the password. When I tried to enter it, the keyboard stopped responding. I tried to delete the password, but Ubuntu isn't letting me. Numbers           and letters don't work, neither does copying/pasting. All I say was a block of text the first time I tried without entering a password.

---

