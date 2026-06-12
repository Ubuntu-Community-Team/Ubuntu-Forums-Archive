---
title: "Gutsy 7.10 wireless  encryption key not accepted"
date: 2008-01-25
forum: Networking &amp; Wireless
---

### Post by drumanart on 2008-01-25
Hi world.
For my "on-board" wireless card (ASUS P5B-MX/WiFi-AP) I installed, using ndiswrapper 1.51, the driver "net2425".With this driver I'm finally able to connect to en unencrypted router and I can navigate. But if I try to connect to my personal router WLAN_86 with my password the card can't connect. On the other hand, if I boot the same PC in Windows XP, with the same password I can connect without any problem to my router. I tried the Network Manager, the Wicd Manager and I tried to configurate the card using the terminal. No way... Searching now for weeks in the Ubuntu forums I still couldn't solve the problem. I'm new in Ubuntu but what I have seen up to now is enough to decide to use the program in future as main operating system. But without access to internet....
I would be very, very pleased if somebody could help.

---

### Post by johnydoe666 on 2008-01-25
we'll need some more info, like: what kind of security does your network feature (wep, wpa, wpa2) and are you perhaps using an obscure combination of security models (like various linksys router models supprt)?

also, what did you try exactly, perhaps there was an error we can make some more of? did you check your logs? 

another thing to check with networkmanager is your keyring manager, see if the faulty key isn't stored there.

---

### Post by drumanart on 2008-01-26
Thanks for replying my thread.
On the back of the router I found this: Wep 128 bite (alfanumericá).
MAC address: 00-01-38-64-99-86
Model: Xavi 768v.

In the Network Manager at the Wireless Settings, Network name (ESSID) I wrote: **WLAN_86**;
Password type: **WPA Personal**
Network password: **xxxxxxxxxxxxx** (to make it work in Windows XP I have to use big letters).
Connection Settings: **Automatic configuration (DHCD)**.

The same configuration I tried using Wicd Manager.

What do you mean with Logs and what is the keyring manager? Sorry I'm brand new in Ubuntu.
If I use the terminal and write: sudo iwconfig wlan0 essid WLAN_86 key xxxxxxxxxxxxx I get the error:
Error for wireless request "Set Encode" (8B2A).
invalid argument "xxxxxxxxxxxxx" - my password.
Thanks

---

