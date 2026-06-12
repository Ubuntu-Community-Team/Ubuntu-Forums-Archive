---
title: "Wireless connection yes or no?"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by matei24 on 2007-07-11
Hello i have recently installed ubuntu on my laptop and i received a wireless connection as soon as i booted. I connected to an access point however i had no internet. I tired configuring the connection manually and entering the wep key that way but no success. I can see a wireless connection in my network setting however when i did $sudo ifconfig i saw no wlan only eth1 and eth0.

Any ideas as of why i cannot access the internet?

---

### Post by bkaskar on 2007-07-11
As you say its visible in network-manager, did you try looking for where is it betting bound to?

'sudo lshw -C network'

also the network you are trying to connect has WEP or WPA enabled? I am having similar issue and ask so because I know I've WPA enabled but the ssid shows up in WEP settings under wireless card's properties

-B

---

