---
title: "[SOLVED] Broke my wireless by messing with aircrack...how to reset?"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by RottenBananas on 2008-02-19
So I tried messing with aircrack and airodump
read a couple guides and tried a couple things...but messed up my wireless internet

i came across this guide for injection and tried it out
[http://aircrack-ng.org/doku.php?id=ipw3945](http://aircrack-ng.org/doku.php?id=ipw3945)

after following the steps my wireless stopped working...i can see any networks in roaming mode
How can i reset my interfaces/drivers to what they were? Im using an intel pro 3945 network card.
didnt really no what i was doing and tried random stuff and the outcome wasnt so great :lolflag:

i thought it mightve been since i was in monitoring mode but i couldnt figure out how to switch to normal mode

i tried sudo airmon-ng stop eth1 but nothing happened

so i completely uninstalled aircrack and rebooted but still no wireless
is there a way to completely reset?

please help

Thanks 
-Bananas

---

### Post by RottenBananas on 2008-02-20
nvm had to run sudo modprobe -r ipwraw and then sudo modprobe ipw3945

Thanks anyway

---

