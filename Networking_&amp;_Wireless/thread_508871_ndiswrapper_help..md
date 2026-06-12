---
title: "ndiswrapper help."
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by JMV290 on 2007-07-24
Well I'm trying to get ndiswrapper working.  I know that on the previous installation I had a few months ago I only had to download one thing and everything worked fine.

I reinstalled Ubuntu the other night and everything is more complicated.    I can still figure it out, except for the part where I download the Windows drivers.

> #
Card: BT Voyager 1040

    *
      Ndiswrapper version: 1.2
    *
      Chipset name: Broadcom BCM4306KFB
    *
      PCIID: 00:09.0 Class 0280: 14e4:4320 (rev 03)
    *
      Windows driver location: Driver: [ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_1500/drivers/80211g.zip)
    *
      Other: Needs both *.inf files in same directory but use BCMWL5A.INF for ndiswrapper driver install.
    *
      Using SuSe 10.0 with AMD Sempron 2200



The link is dead. Are there any mirrors up?

---

### Post by yorkie on 2007-07-24
Heres a video about installing ndiswrapper on ubuntu and the files you need

[http://www.youtube.com/profile_videos?user=AlexanderGrim&p=r&page=2](http://www.youtube.com/profile_videos?user=AlexanderGrim&p=r&page=2)

its installing ubuntu part 2
its very good

---

### Post by kevdog on 2007-07-24
I know the link is dead, but I think you can google around and find it.  If you have Windows XP drivers for your card you can use those too.  The link is really for people that dont have any drivers.  If you cant find the acer drivers, search in the forums for broadcom 4306 chipset revision 3 and pm the people who wrote the posts to see if they can send you the drivers.

---

### Post by TechMage89 on 2007-07-24
Shouldn't that chipset work with the bcm43xx drivers? Why do you need to use ndiswrapper?

---

