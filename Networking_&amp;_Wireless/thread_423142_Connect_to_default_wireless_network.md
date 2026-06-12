---
title: "Connect to default wireless network"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by stchman on 2007-04-25
Hello all, I have a question about wireless.

I have my router and laptop setup with network-manager and WPA2 wireless encryption.

Only thing is that when I boot up the laptop Ubuntu wants to connect to the strongest non-secure wireless network which is my neighbor.  How do I specify a default wireless network?

Thanks

---

### Post by spd106 on 2007-04-26
Try this link [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

---

### Post by nhidog on 2007-04-27
I would like to know as well, tried the method mention in the link but it doesn't help.  Curse my lousy fingers and choosing my neighbor unsecure wireless network before my own...now everytime I log in, I have to switch to my network.  Help!...I really have the urge to change his SSID :).

EDIT: I think I found it /home/yourname/.gconf/system/networking/wireless/networks.  I removed the offending SSID directory and going to reboot and pray.

-Nhi

---

### Post by dapaintballer331 on 2008-03-26
Wow, thank you. I had the same problem, it always tried my neighbors wireless connection first.

---

