---
title: "Help!!!!!! Please Help!!"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by dontke on 2007-04-24
Hey I recently installed Ubuntu on my laptop after getting frustrated from receiving 5 blue screens in windows. I had a 2wire wireless card working in windows but I have had a big problem trying to make it work in Ubuntu. I tried installing ndiswrapper, and WPA but none of them seemed to work with this wireless card all it does is get the link light on. I already installed the windows drivers(.inf files) in ubuntu using System>Administration>Windows Wireless Drivers but still cant get the card to connect. I have the wired connection card connecting to the internet easily on the same PCMIA port I plug the wireless card, so I know for a fact its not the port with the problem. Just before I posted this, I tried again to plug the wireless in the port but for some reason this time, the link light on the card doesnt go on. After doing ndiswrapper -l this is the output i get

name@Dmoney-laptop:~$ ndiswrapper -l
Installed drivers:
wlanuig driver installed, hardware present

---

### Post by dannyboy1121 on 2007-04-24
Hmm - my guess would be the authentication. Are you using a pass phrase to connect ?? If so - what happens if you swap that for the hexidecimal equivalent ?

---

