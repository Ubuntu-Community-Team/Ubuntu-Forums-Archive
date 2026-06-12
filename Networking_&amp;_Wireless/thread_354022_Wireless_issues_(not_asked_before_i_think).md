---
title: "Wireless issues (not asked before i think)"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by EttanA on 2007-02-05
Hi guys, I dont think this has been asked before, but I'm in a bit of a hurry atm and I just cant wait until tomorrow ^^

I just recently found a guide on how to enable wireless using firmware (not ndiswrapper at all). I have previously used ndiswrapper, blacklisted bcm43xx etc as most of you probably know. And about an hour ago I tried the firmware version, cant find the guide atm but im sure you know which one I mean.

Anyways, my blue LED light started shining for the first time in days, and i was so happy after installing with the new approach :) But to my dispair, i cant seem to find any wireless networks to connect to, not using any of the wireless programs you can download (Wifi-something, network manager, etc...). I have another laptop with windows, and when I check available wireless networks there I find like 3-4 (neighbours ^^), but here I cant find a single one. It cant be the signal, I've tried it with the other computer right next to this one.. so what might be the problem? Could it be something I did with ndiswrapper? Should I just reinstall Ubuntu totally and try again with this technique right away? I havent had time to configure the system alot, so a clean new install of the OS wouldn't hurt very much, but i dunno if it will help.

Any comments would be great.

Oh btw, Im using a bcm4310 Broadcom network card, sitting on a HP nx6325 laptop.

---

### Post by EttanA on 2007-02-05
Bumping this thread in case someone else has the same problem. I managed to fix it (I think) by adding ndiswrapper to blacklist. However, I think something went wrong, because now I can't open the OS sometimes, but that's not my main concern now, I'm sure I can fix it with a  reinstall of the OS, now I know what way to install the network drivers. 

My new problem is that I actually manage to connect to the internet (all the available nearby connections show up in the list (using Wifisomething)), however the connection only lasts for about a minute before the signal seems to fade and after a while completely stop working. What might be the cause of this? Seeing as I can find the networks at first, but the speed gets slower and slower, and after a while all the other networks disappear from the list, and I can't access any webpage anymore. Thankful for answers, going to bed now :)

---

