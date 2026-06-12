---
title: "[SOLVED] I'be been fighting for the last two days, I need help"
date: 2007-07-29
forum: Networking &amp; Wireless
---

### Post by Fallen_62 on 2007-07-29
So, I had my wireless working (BCM4306) before I had to reformat my Linux partition because I did some playing and messed up my display a little bit.  Anyway, it was working, but I had used ndiswrapper (but I dont know if it actually was ndiswrapper or the fact that I updated to Fiesty 7.04)

Anyway, I got everything reformatted, updated, etc, and in my tinkering before, I found out that the default bcm43xx driver worked for my card.  Now, my card can see the wireless routers, but it wont connect to them.  Is there something that I can type in the command line (other than iwconfig eth1 ap <mac addy>) to connect to one...?  I downloaded a few wireless network managers, and they both can see the routers, but they cant connect.  I can also scan in the terminal and see them, but I dont know how to connect to them or what is wrong.

Any help (either in network managers or troubleshooting) would be greatly appreciated.  I can give you more detail if need be.

---

### Post by LuisAugusto on 2007-07-29
bcm43xx driver needs the firmware, which is on the repos, I assume you already install it.

Are you trying to connect to wireless spots whit WEP?

---

### Post by jdavila27 on 2007-07-29
I think I have the same wireless card, but I had to install ndiswrapper to make it work. My laptop is an hp pavillion ze5300 and I downloaded the windows driver from hp.com

I also configured the card so that roaming was enabled

---

### Post by Fallen_62 on 2007-07-29
> **LuisAugusto said:**
> bcm43xx driver needs the firmware, which is on the repos, I assume you already install it.

Are you trying to connect to wireless spots whit WEP?

I installed it before I did the updates, I didnt think of installing it after...  I can give it a try.

I hope I dont have to do that, jdavila.  Last time I used ndiswrapper i dont know how I got it to work O.o

---

### Post by LuisAugusto on 2007-07-29
Ok, but, are you trying to connect to encrypted wireless networks? As far as my experience goes whit broadcom, the network manager way doesn't work whit those.

If using the bcm firmware from the repos doesn't work, you'll need to use ndiswrapper

---

### Post by Fallen_62 on 2007-07-29
> **LuisAugusto said:**
> Ok, but, are you trying to connect to encrypted wireless networks? As far as my experience goes whit broadcom, the network manager way doesn't work whit those.

If using the bcm firmware from the repos doesn't work, you'll need to use ndiswrapper
No, it's not an encrypted network.  I have the MAC filter set to allow only the ones in the list, and this one is in the list.  I can connect to it fine in WinXP.  I cant connect to a completely open connection, either.

And the firmware didnt work.  Is there any driver that is supposed to display in the Windows Wireless Drivers...?  Because I dont, but I dont know where to find the bcm43xx driver to put it in there...

---

### Post by LuisAugusto on 2007-07-29
> **Fallen_62 said:**
> No, it's not an encrypted network.  I have the MAC filter set to allow only the ones in the list, and this one is in the list.  I can connect to it fine in WinXP.  I cant connect to a completely open connection, either.

And the firmware didnt work.  Is there any driver that is supposed to display in the Windows Wireless Drivers...?  Because I dont, but I dont know where to find the bcm43xx driver to put it in there...

Whit ndiswrapper you need your Windows Driver

---

### Post by Fallen_62 on 2007-07-29
I took off ndiswrapper and tried it, and it was no good.  Then I messed something up, so I reformatted again.  Im on a clean Feisty install, and my wireless can scan networks, but it cant connect to them.  Says it cant get an IP address.

Edit:  I think I got it fixed.  I didnt need to use NDS Wrapper...  I set something different on my router, restarted my computer, and then it worked.  I think that it was my router...  Which makes me mad.  But anyway, I got the wireless to work, without ndiswrapper :D  Thanks for the suggestions all!  I appreciate the help, but it seems that it was my own carelessness that prevented me from getting it to work.

---

