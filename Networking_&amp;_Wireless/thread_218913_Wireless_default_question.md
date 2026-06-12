---
title: "Wireless default question"
date: 2006-07-19
forum: Networking &amp; Wireless
---

### Post by kurbacik on 2006-07-19
I want to boot my computer with the wireless interface deactivated by default, and then activate it when necessary. How can I add this modification? I've modified the wireless interface as wlan0, instead of eth1. Could there still be some commands that activate this interface when I boot? This is my doubt because even if I deactivate the wireless interface with "System->Administration->Network Settings", it appears as activated when I reboot the laptop. I've configured my laptop (AMD64 HP Pavilion zv5000) with ndiswrapper. Other than this problem, the wireless works perfectly.

---

### Post by Titus A Duxass on 2006-07-19
You need to add ndiswrapper to /etc/modules - do this in a terminal.
Then you need to modify your /etc/network/interfaces file and change any eth0 settings to wlan0 and add auto wlan0 at the end of the file.

Search for an example of the interfaces file.

Then do a cold restart.

---

### Post by kurbacik on 2006-07-19
I followed your suggestion, but I still have the same previous behavior for the wireless card. :confused:

---

