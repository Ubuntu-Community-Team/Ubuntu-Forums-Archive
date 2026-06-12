---
title: "[SOLVED] Atheros wireless BG died! EEEK!"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by aschaetter on 2008-03-13
My Toshiba Satellite A135-4656 (Kubuntu Gutsy) has had some serious network issues for the past week. After it died, I tried to install the newest madwifi drivers to no avail. The network manager doesn't go into offline mode on its own anymore. It always shows that the network cable is plugged in. For some reason, it tells me that there's no active devices either, and I do get IP through the wired lan. I can manually scan for and find APs using iwlist.

I'm on my last nerve with this, so if anyone has any ideas, please share. I am NOT reformatting my poor laptop.

---

### Post by burnclouds on 2008-03-13
Are you using Network Monitor (N.M.)>

---

### Post by aschaetter on 2008-03-13
I'm not familiar with network monitor. I've got knetwork-manager installed though.

---

### Post by aschaetter on 2008-03-14
Bump

---

### Post by aschaetter on 2008-03-14
Good news! After a 6 hour road trip, my drivers are installed and I'm on the wireless network at the hotel right now. I still can't get knetwork-manager to work correctly though. How in the world, does the network manager interface with the network cards???

---

### Post by aschaetter on 2008-03-15
If anyone was wondering.... /etc/network/interfaces shouldnt have your laptop's wifi or wired lan listed if you want network manager to work correctly.

Becoming more competent FTW!!!

---

