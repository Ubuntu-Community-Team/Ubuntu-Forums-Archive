---
title: "madwifi and injection with WG511T"
date: 2008-04-21
forum: Networking &amp; Wireless
---

### Post by mrbuntuman on 2008-04-21
Btw i been reading alot post regarding "patching madwifi" for injection and monitor mode. 
Let me make it very easy for you.

Im running 7.10 Ubuntu and u dont have to do anything to patch ur dirver

u only need to type a fw line of code .

apt-get wifi-tools
apt-get aircrack-ng

wlanconfig ath0 destroy
wlanconfig ath0 create wlandev wifi0 wlanmode monitor

now u should have ath1 in mon mode

aireplay-ng -9 ath1 (injection test)

than ur good to go.

i use 2 card 1 for mon and one for injection , however this should get the wg511t boyz and girlz started.

cheers

---

