---
title: "2wire wireless card"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by dontke on 2007-04-17
Hey I recently installed Ubuntu on my laptop after getting frustrated from receiving 5 blue screens in windows. I had a 2wire wireless card working in windows but iI have had a big problem trying to make it work in Ubuntu. I tried installing ndiswrapper, and WPA but none of them seemed to work with this wireless card all it does is get the link light on. I already installed the windows drivers(.inf files) in ubuntu using System>Administration>Windows Wireless Drivers but still cant get the card to connect. I have the wired connection card connecting to the internet easily on the same port I plug the wireless card, so I know for a fact its not the port with the problem. Just before I posted this, I tried again to plug the wireless in the port but for some reason this time, the link light  on the card doesnt go on. Please help!!!!!!

---

### Post by Kobalt on 2007-04-17
Can you please post the output of the following command line : ```
ndiswrapper -l
```

---

### Post by tturrisi on 2007-04-17
You don't need ndiswrapper for 2wire cards.  The 2wire has an agere chipset & uses the orinoco & hermes drivers.  The 80211-b cards use WEP only.   If your 2wire is the g card, then I believe it has a broadcom chipset & will require ndiswrapper w/ windows drivers.

---

### Post by dontke on 2007-04-19
Thanks for your reply, when I typed ndiswrapper -l this is the output i got but the link light on the card is not lighting like before I dont know whats wrong.

name@Dmoney-laptop:~$ ndiswrapper -l
Installed drivers:
wlanuig         driver installed, hardware present 

tturisi: Im not a linux expert so i dont know what is the right chipset that goes with this card. Please  explain more on what you mean.

---

### Post by dontke on 2007-04-19
The output for the ndiswrapper is
name@Dmoney-laptop:~$ ndiswrapper -l
Installed drivers:
wlanuig         driver installed, hardware present

---

