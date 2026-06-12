---
title: "Resetting SSID Log?"
date: 2015-07-24
forum: Networking &amp; Wireless
---

### Post by sdharrison.9 on 2015-07-24
Last night I wanted to set up an old router I had laying around for a project. That router had the same SSID as my current main router. When I was finished with my spare router (it is now completely unpowered/ unplugged) I attempted to connect to my main router with limited success. Only 20% of pings succeed. 'watch -n.2 iwconfig wlan0' shows a momentary connection and then no connection every couple refreshes. The most suspicious 'dmesg' shows "cannot understand ECSA IE operating class 33, disconnecting".

My thought is that somewhere there is information about the old router that conflicts with my current router? Need advice on how to completely reset everything related to networking.

The initial change from the old router to the current router was several months ago, and setup has been rock solid until I powered up the old router.

---

### Post by chili555 on 2015-07-24
I suspect it's in /etc/NetworkManager/system-connections/. You might remove everything in it, restart NM and see if your connection improves:```
sudo rm -rf  /etc/NetworkManager/system-connections/*
sudo service network-manager restart 
```You'll probably have to resupply your security key.

---

