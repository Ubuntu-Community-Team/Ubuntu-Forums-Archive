---
title: "AR5212 and monitor mode"
date: 2007-03-06
forum: Networking &amp; Wireless
---

### Post by zupermanz on 2007-03-06
My wireless card (TLWN610G) works out of the box in ubuntu 6.10, but i have a problem: I cant use it with airodump and airodump-ng because i cant turn monitor mode on.
I have the restricted pacages installed.
I have a celeron 1600 (amilo-d) with a wireless incorporated.
Kismet seems to work.
The strange thing is that airodump-ng works in windows!
Thanks in advance

---

### Post by airbornespent on 2007-03-27
Hi, with the madwifi drivers you must create a new interface in monitor mode with wlanconfig.
First you need to destroy the current interface with:
wlanconfig athX destroy (where X is the number of your current interface)
Then you create a new interface in monitor mode with:
wlanconfig ath create wlandev wifi0 wlanmode monitor (you can place a 0 or any interger after ath to create ath0, ath1, ath18 etc...)

This creates an interface in monitor mode and works successfully on my 6.10 install. However, I haven't been able to get airodump to see any traffic. I was looking for an answer to that problem when I saw your post. Let me know if you have any success.

---

