---
title: "Atheros Wireless not working"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by sharondenscabbia on 2008-12-15
Hello

I am having problems with my Atheros wireless card. I am using Ubuntu 8.10, it appears to be picking up my card (it is visible under system/administration/hardware drivers)but it isn't picking up any wireless networks. (Vista finds 7) 

After much googling, I've been pointed to [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html) to solve it. However, when I try to compile it, it can't find any makefile.

Could anybody help me?

Thanks,
Sharon

---

### Post by ja660k on 2008-12-15
you need ndis wrapper, contrary to what people say, you do not need to use madwifi.

just make sure you can get hold of your windows driver.

program files->Atheros->Driver
and you need the .inf

now that you have that.  back in GNOME 
system->administration->Hardware drivers

and make sure that both Atheros hardware access layer AND support for lan card are NOT enabled, so unchecked

then you can go ahed and install the driver through ndiswrapper.
then little led might not change colour when your connected but thats just cosmetic

---

### Post by ja660k on 2008-12-15
you need ndis wrapper, contrary to what people say, you do not need to use madwifi.

just make sure you can get hold of your windows driver.

program files->Atheros->Driver
and you need the .inf

now that you have that.  back in GNOME 
system->administration->Hardware drivers

and make sure that both Atheros hardware access layer AND support for wlan card are NOT enabled, so unchecked

then you can go ahed and install the driver through ndiswrapper.
then little led might not change colour when your connected but thats just cosmetic

---

### Post by bumanie on 2008-12-16
I used ndiswrapper to get an atheros wifi card working in my laptop. I believe if you enable backports in software sources the drivers for the card will be downloaded. Atheros cards worked fine in 8.10 beta, until a partial kernel upgrade during the release candidate stage - Try backports if that doesn't get the card working, ndiswrapper will.

---

### Post by nhasian on 2008-12-16
yes you should enable the backports.  also follow the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by sharondenscabbia on 2008-12-16
I've downloaded and installed the atheros driver in ndiswrapper, and it says "hardware present: yes". However, it still doesn't seem to pick up any wireless networks. Either this, or I don't know how to find them!

Could anybody please shed the light?

Thanks,
Sharon

---

### Post by carml on 2008-12-16
Me too I encountered a problem with my Atheros,and me too I installed ndiswrapper;make sure that under System->Administration->Hardware Driver both Hal or support for 802 lan are uncecked.This is what you have to do,if I don't remember wrong what I did to get the wireless work.:popcorn:

---

### Post by sharondenscabbia on 2008-12-16
> **carml said:**
> Me too I encountered a problem with my Atheros,and me too I installed ndiswrapper;make sure that under System->Administration->Hardware Driver both Hal or support for 802 lan are uncecked.This is what you have to do,if I don't remember wrong what I did to get the wireless work.:popcorn:

Under Hardware Drivers, there is only 802 lan, and its unchecked. As far as I can tell, all has been followed to the letter...

Sharon

---

### Post by sharondenscabbia on 2009-01-11
I apologise for the long period of inactivity, I went somewhere where there was no wired internet access, and as such, couldn't get online. I have tried endless things during this time to get my wireless to work, with no luck. I'm convinced I've tried all the advice here to the letter.

Unless there is some ambiguity in the previous posts, which may mean I've made an error in trying to fix this, does anybody have any further ideas? I'm tempted to just go out and buy a wireless USB dongle...

Thanks,
Sharon

---

