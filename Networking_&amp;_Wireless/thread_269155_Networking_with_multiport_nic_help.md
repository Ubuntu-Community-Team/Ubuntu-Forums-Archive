---
title: "Networking with multiport nic help"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by drewk1 on 2006-10-01
I have a pc running Ubuntu connected to the internet via an ethernet adsl modem.
This pc is fitted with a four port ethernet card and what i would like to do is share the internet connection to 3 other windows pc's on my network, each one in its own seperate port on the muti card.

The unbuntu box sees the multi card ports ok as eth1-4 with eth0 being the internet connection ( on another ethernet port )

What I need is some guidance on how the get the whole thing working.

Any help would be appreciated.

---

### Post by mips on 2006-10-01
You wil have to configure each port to be in a seperate network.

ie Eth0 -> 192.168.0.0
Eth1 -> 192.168.1.0
Eth2 -> 192.168.2.0
Eth3 -> 192.168.3.0

Each pc connecting to these ports will have to be configured with corrosponding IP information.

Next you will have to enable routing in order for these PC's to get to the internet.

Look at this as a guideline, [http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

### Post by drewk1 on 2006-10-01
Thanks very much

That looks like the info i'm looking for, time to have a read and play :D

---

