---
title: "Wireless stopped working"
date: 2006-11-03
forum: Networking &amp; Wireless
---

### Post by zeeR on 2006-11-03
I use network-manager to connect to my wireless network, and it all went fine, it found the network and connected easily...the problem is that, after the internet being down for an afternoon (ISP problems, i checked on windows and it couldn't connect too), i can no longer connect! On that afternoon,it connected and the first green light turns on, but the second one never did...But now, everything is ok and this keeps happening.I thought that maybe the isp still had problems, but when i logged on to windows, it connects with no problems...I tried clearing up the interfaces file, and it is just as it should be...i tried connecting  through ubuntu's administration/networking, and nothing happens..i click enable, insert the password and the ESSID, and it just sits there, doing nothing...the bar that should appear when connecting doesn't show up...=\ i'm really desperate,cause without internet,ubuntu is of little use for me...and nothing seems to be wrong, i can't understand why it doesn't work...

I'm on edgy, btw.

Any help would be appreciated, and sorry for my english..;)

---

### Post by zeeR on 2006-11-03
sorry bumping this, but i really need help =\ without internet, there is no reason to keep ubuntu, since i can't install software, upgrade, IM and browse the web =\ i'd really like to know what happened...thank you

---

### Post by oo00oo on 2006-11-03
Hi, what is your wireless card because sounds like you are having the exact problem I was... do you have a D-link card? I have a D-link DWL-G122 and using the default Ubuntu driver the green link light stays lit but nothing else!

I have to unload the ubuntu driver and use my own driver to get it to work...which I can tell you how if you have the same wireless card?

Matt

---

### Post by zeeR on 2006-11-03
> **oo00oo said:**
> Hi, what is your wireless card because sounds like you are having the exact problem I was... do you have a D-link card? I have a D-link DWL-G122 and using the default Ubuntu driver the green link light stays lit but nothing else!

I have to unload the ubuntu driver and use my own driver to get it to work...which I can tell you how if you have the same wireless card?

Matt

Hi! I have an Intel 2200 wireless card...the problem is, linux HAS drivers for it, it worked perfectly before...i don't know why it got screwed up now...=\

---

### Post by oo00oo on 2006-11-03
Well I cant tell you the drivers to use instead because I don't have that card. But I can see your problem. Mine messed up when I upgraded to 6.10. 

Try  reinstalling the drivers is my suggestion, my card seemed to suffer the same problem as yours and that worked for me. You will probably have to unload your old driver (modprobe -r [driver name]) then call your new driver... Good luck!

---

