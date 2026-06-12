---
title: "Hidden Wi-Fi not connecting under KDE"
date: 2015-06-07
forum: Networking &amp; Wireless
---

### Post by jim50 on 2015-06-07
Hi allI'm having the problem that the hidden wifi: 'Company's netork' will not join in KDE. it is seen as a hidden network, I click on it and click return, enter the wpa2 password and it then starts connecting, gets as far as 'configuring' then just shuts down to 'not connected'Any ideas?Thanks

---

### Post by jim50 on 2015-06-07
Solved!
I'll post the solution incase anyone needs it:

You need to tell the system to search for the name from the command line, not the knetwork manager:
```
sudo iwlist  scanning essid  <network name>
```
so on my system
```
sudo iwlist wlan0 scanning essid Bob\'s\ network
```
if you dont have iwlist, you need the internet tools for linux package.

Jim

---

