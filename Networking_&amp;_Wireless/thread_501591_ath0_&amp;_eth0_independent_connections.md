---
title: "ath0 &amp; eth0 independent connections"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by jerseygeek on 2007-07-15
i'm pretty new to linux and i want to know if there's a way to have 2 independent network connections.  my friend lives 2 apts away and we'd like to be able to share files.  he's got a wireless network i can connect to and i have my own wireless network.  i want my ubuntu machine (sony vaio laptop) to be able to use his internet (he has fios) through the wifi card (ath0) and just connect to my network through the embedded rj45 (eth0).  i don't want to bridge. i just want some programs (like azureus) to use his network but still be able to see and use my network in general. is this possible?  if so, how?

---

### Post by rjfioravanti on 2007-07-15
You should be able to just do this through system->admin->network

Enable both connections and set them appropriately 

Then type ifconfig to see if you have gotten ip address on both interfaces

---

### Post by jerseygeek on 2007-07-16
thanks for the response.  I had them both connected and they each had addresses on the respective networks (192.168.42.* and 192.168.37.42 [one is static and the other is dhcp]) but when they were both active i couldn't get a connection to the internet.  should one be set as a primary or default somehow?

---

