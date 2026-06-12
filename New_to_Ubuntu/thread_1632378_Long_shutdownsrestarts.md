---
title: "Long shutdowns/restarts"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by brando435 on 2010-11-27
Ok, for some odd reason, whenever i try to restart Ubuntu 10.10, it takes forever to shut down or restart (and sometimes doesn't shut down or restart at all), i have no clue why. I'm duel booted with Windows 7 Ultimate, and Ubuntu 10.10 using Wubi. and also another problem I'm having is my Wifi, (i have an Atheros Driver) and it won't pick up Wireless, im running Ubuntu 10.10 right now using an ethernet cable from afriends house. and i also heard of MadWifi, but idk how to set it up :( Please help!!!

---

### Post by mikewhatever on 2010-11-28
How much space did you allocate to Ubuntu? Little space and consequently hight fragmentation may be the cause of long startups and shutdowns. Can you post the output of the **df -h** command from Ubuntu.
As for the wireless, check out the troubleshooting guide.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
Check if there is a driver for your card under System->Admin->Drivers.

---

