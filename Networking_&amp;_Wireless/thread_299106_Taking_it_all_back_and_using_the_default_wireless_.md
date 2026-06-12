---
title: "Taking it all back and using the default wireless config."
date: 2006-11-13
forum: Networking &amp; Wireless
---

### Post by neobonzi on 2006-11-13
I recently upgraded to edgy and everything was working find until i tried to start up my wireless and realized it didnt appear in the network settings window. When i looked in the device manager it appears correctly as a Intel 3945ABG Wireless Card.

  I was led to the solution of ndiswrapper and went through the whole ordeal of compiling it myself (because apparently it wont work with edgy if you dont) and installing the wireless windows driver from my dell CD. This failed because after 3 or 4 minutes the kernel would crash (aka the entire desktop and keyboard/mouse would lock up and id have to kill the power to restart) every time i used modprobe to enable the wireless.

  I noticed that my card, the 3945ABG, is supposed to work with Edgy out of the box (others on this forum and on irc claim to be messanging me from their edgy, 3945 wireless enabled dell laptops). My question is - is there anyway i can take it all back (get rid of ndiswrapper, i already deleted the driver that crashed my comp) and use whatever Ubuntu originally comes with? How do I use the driver made for linux instead of the windows one? Thank you guys so much for any help - i'm having fun learning all about linux through all the things im messing up in it :D.

---

### Post by neobonzi on 2006-11-13
this is the driver i refer to when i talk about "using the driver made for linux" - [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

There's one that comes with Ubuntu - I'm sure - because i used it on 6.06

Any ideas? When i try to install the one from [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) i get an error about a problem with IEEE which im sure i dont want to mess with (considering my problems with ndiswrapper) :D
](*,)

---

### Post by rvickers on 2006-11-13
I have the same wireless card and tried so many things to get it to work in edgy that even my wired quit working. I finally formatted and reloaded ubuntu. I'll wait until the ubuntu people come up with a fix before I try that again:rolleyes: . There's just too many people having wireless issues right now. 6.06 was fairly reliable though. Good luck...

---

### Post by neobonzi on 2006-11-14
It seems sad that thats the only solution! I'm sure theres some way to get it to work - especially when theres an official intel driver for linux! I hope someone can maybe tell me how to install the linux driver?

---

### Post by Yeuclid on 2006-11-14
Not the same driver, but I eventually got a stable connection by discarding NDISwrapper, and using the WLAN-NG package.

It maybe worth a try

---

### Post by neobonzi on 2006-11-14
awesome! is there a link you can give me or provide me with some sort of direction on how of setting that up? I'm guessing its just in synaptic? Thanks a lot bud

---

### Post by neobonzi on 2006-11-14
After some intensive reading im beginning to wonder whether the failure of my wireless driver has anything to do with the fact that I have a Dual Core Pentium CPU? If i switched to the 386 kernel would that have any effect on my wireless?

---

