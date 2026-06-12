---
title: "broadcom BCM4318 AirForce One 54g"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by cwscllc on 2007-03-14
I am having a problem finding a driver for my wireless, ethernet, and network cards.  I looked up the broadcon page but it didn't help.  I viewed the list of drivers supported by ubuntu, and saw broadcom, but didn't see 4318.  I have a dell inspiron 1300.  Is my pc not supported? What is my next step?

---

### Post by DarkN00b on 2007-03-14
I have that chipset in my Linksys card. Take a look [here]("http://ubuntuforums.org/showthread.php?p=1071920&mode=linear") for native Ubuntu support. No need for Ndiswrapper.

---

### Post by carloscuny on 2007-04-29
As an inspiron 1300 owner  i've had with ndiswrapper in dapper wireless with the broadcom 4318 minipci wireless card.
Since feisty fawn (7.04) I'v lost it and i can't make it work. Not in Ndiswrapper + windows driver, or the native thing, which should work out of the box.
there're a lot of different solutions and i tried a lot of them ndiswrapper and several drivers, blacklisting the original driver that came with feisty but finally gave up, cause  it took me too much time.   :( 

At this stage i wonder wether replacing the thing (broadcom4318 minipci) with a better supported one (Intel?)
or MSI with ralink chipsets is a better idea then investing in broadcom


Does anyone have good results with replacement
Futher: there's np pcmcia card but a expresscard, still i can't find any wifi card supported by Ubuntu and i guess the minipci still is my best shot?

Broadcom is knowm not wel supported and not cooperative for open software so......

---

### Post by ChuxMix on 2007-04-29
I struggled with my Broadcom 4318 and followed some of the howtos on the forums here with no luck, then I found this:

[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=5)

It worked prfectly the first time, and wasn't too complicated!
I use it in conjunction with Wifi Radar and now wireless is a pleasure instead of a pain.

---

