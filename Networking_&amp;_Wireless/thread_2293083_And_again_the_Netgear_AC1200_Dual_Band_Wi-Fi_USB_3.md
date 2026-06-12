---
title: "And again the Netgear AC1200 Dual Band Wi-Fi USB 3.0 Adapter"
date: 2015-09-02
forum: Networking &amp; Wireless
---

### Post by Ken_Snyder on 2015-09-02
Hi,

yesterday i bought an Netgear AC1200 Dual Band Wi-Fi USB 3.0 Adapter that works pretty cool on windows boxes up from XP to 10 (tested by my self today) , but i personally wanted to use it on a linux system, preferable on a kubuntu system with the latest 4.2 stable kernel. Its a really powerful piece of hardware due to its strong antenna and with a ac capable router it extended my working range in our home. So far i am happy with it. I sadly found out, that there is no current working linux kernel module for it available and digging in the web didnt reveal some working driver for it. Trying to use some windows xp driver with ndiswrapper wasnt successful either (driver imports unknown symbols for the ndiswrapper). Extracting the right device drivers from the windows installer was pretty painful too. So i started to look for (older) similar (windows) drivers but they all link to kernel library functions that could not be handled by the ndiswrapper. BTW i am aware of this post and all the links inside it here:

[http://ubuntuforums.org/showthread.php?t=2265150&highlight=Netgear+AC1200](http://ubuntuforums.org/showthread.php?t=2265150&highlight=Netgear+AC1200)

But it looks like that MediaTek indeed did release some open source code for the chipset[/SIZE][SIZE=2] MT7612U [/SIZE][SIZE=2]of that device:

[http://www.mediatek.com/en/downloads1/downloads/mt7612u/](http://www.mediatek.com/en/downloads1/downloads/mt7612u/)

And here comes the question: How do i compile this into a working, lodable ko module? Where to start?
 

Ken

---

### Post by joni-palosaari-0 on 2015-09-03
[http://ubuntuforums.org/showthread.php?t=2265150&p=13227958#post13227958](http://ubuntuforums.org/showthread.php?t=2265150&p=13227958#post13227958)
No can do. I have netgear wnda3100v3 with same chipset and no luck. I managed to fix first compile errors by refactoring two lines of the code, but then just got LOTS of more errors so I quit. Atleast it compiled more.. so if you want it to work, you have to fix drivers by yourself.  Maybe we should try older kernel, like ~3.10. But it probably only fixes those two lines. But who knows. What kernel are you use? Im with 3.18 on gentoo, cause of nvidia. 

Second chance is to contact p4plus2 on gentoo forums. I think he managed to fix more code than me. See the second last post here [https://forums.gentoo.org/viewtopic-p-7727920.html](https://forums.gentoo.org/viewtopic-p-7727920.html)

---

### Post by Bucky Ball on 2015-09-03
Please use default font and point size. Can't help, but have bumped your thread. That card is notoriously painful.

---

### Post by Ken_Snyder on 2015-09-03
> **joni-palosaari-0 said:**
> [http://ubuntuforums.org/showthread.php?t=2265150&p=13227958#post13227958](http://ubuntuforums.org/showthread.php?t=2265150&p=13227958#post13227958)
No can do. I have netgear wnda3100v3 with same chipset and no luck. I managed to fix first compile errors by refactoring two lines of the code, but then just got LOTS of more errors so I quit. Atleast it compiled more.. so if you want it to work, you have to fix drivers by yourself.  Maybe we should try older kernel, like ~3.10. But it probably only fixes those two lines. But who knows. What kernel are you use? Im with 3.18 on gentoo, cause of nvidia. 

Second chance is to contact p4plus2 on gentoo forums. I think he managed to fix more code than me. See the second last post here [https://forums.gentoo.org/viewtopic-p-7727920.html](https://forums.gentoo.org/viewtopic-p-7727920.html)

Hi,

thats exactly the point! I couldnt fix all those compilation errors, telling me member of struct is missing etc. Once you manage to fix one, you get two more errors on next comp run. I am running latest stable kernel 4.2 SMP 32-Bit on my system. I guess some really experienced guy with good C, Assembler and (networking) driver skillz should have a look at this. Too bad that chip isnt supported yet, though it is a very powerful device to run

best

---

