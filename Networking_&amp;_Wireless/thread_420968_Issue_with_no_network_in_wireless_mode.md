---
title: "Issue with no network in wireless mode"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by jeremy12 on 2007-04-24
So i finally got fed up with XP locking up on my laptop so i wiped it and installed 7.04 onto it everything is going great i had 1 issue getting wireless up and running all i had to do was run ndiswrapper from [http://ubuntuforums.org/showthread.php?t=197102&](http://ubuntuforums.org/showthread.php?t=197102&)

but now when i Plug my laptop in using a Ethernet cable i can go Places>Network and see my XP media center box and ubuntu server samba shares, how ever when i unplug from the Ethernet and use the wireless i cannot see anything in the places>network

both wired and wireless are setup with a basic static setup of:
IP: 192.168.1.110
subnet 225.225.225.0
gateway: 192.168.1.1

the server box is setup to a static 192.168.1.115 and when in wireless i cannot even ping the machine

---

### Post by spd106 on 2007-04-25
You should have a different IP address for each interface. Otherwise the arp caches will get confused. You will probably also have routing problems since you should only have one default route at any one time.

---

