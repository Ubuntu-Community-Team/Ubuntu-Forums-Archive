---
title: "Firestarter Firewall fails to start with wireless"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by newbiefromwindows on 2007-07-21
I can start firestarter fine if I am physically connected to the Internet. However, when I connect through wifi, it does not work. I click start firewall and gives me a failure message; Failed to start the firewall. The device eth0 is not ready. Please check to make sure your Internet connection is active (it is).

 Why would this be/ how do I fix it?

---

### Post by Floppyjoe on 2007-07-21
You need to go into the firewall preferences and change the adapter from eth0 to the wireless one which may be wlan0 or some other name.

---

### Post by evolving_monkey on 2007-07-28
I am having the same problem. I have changed the settings in the firewall to point to the wireless card. I can connect to the internet and the network until I try to start firestarter. Then I can only connect to the internet, not the network. Everything is fine when I use the ethernet connection..   

I did notice that it describes my D-Link WDA1320 wireless card as 'Unknown device (wifi0)'
It also lists a third option that I do not recognize "Unknown device (ath0)' 

I'm hoping someone can point us in the best direction to get firestarter going with the wireless card.

Thanks for your time.

---

### Post by evolving_monkey on 2007-07-28
I think I figured It out. I added madwifi-tools (which is in the repositories) also added hostapd under suggested. I didn't add bridge-utils because I don't think I need it as I probably will only have the wireless hooked up and not both connections at the same time, 

Then in the network settings for firestarter a actually selected 'Unknown device (ath0)' instead of the wifi one. Firestarter started up with no error.  I think the (ath0) option might be referring to the Atheros chipset on my wifi card (just a guess). Anyway, it works.

---

