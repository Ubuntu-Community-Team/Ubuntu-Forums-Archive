---
title: "[SOLVED] How to get my wireless conection working?"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by qwallis on 2008-07-02
I need some suggestions as to how to get wireless working.
It used to work fine but as the computer (up to now) has sat next to the router I have used a LAN cable.
The problem is now I want to move the computer to the workshop, where I would be going online via a friends wifi connection located the the adjacent building, so a LAN cable is not an option.

Now, when I plug in the wifi stick (Fritziwlan USB stick) and try to connect, either but choosing the wifi connection that used  ton work, or dropping the LAN cable, the icon in the notification area indicates that it is trying to connect but never gets there and doesn't quit. The computer then becomes unresponsive and requires a re-boot.

:-? Any suggestions?

Cheers

---

### Post by superprash2003 on 2008-07-02
does the connection require a WEP or WPA key?? go to the terminal and type iwconfig and post output here

---

### Post by qwallis on 2008-07-02
> **superprash2003 said:**
> does the connection require a WEP or WPA key?? go to the terminal and type iwconfig and post output here

Yes the connection uses one of them (WEP I think).
Here is the output of iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

Segmentation fault

I should mention perhaps that after entering iwconfig in terminal the computer hangs and I can't do anything with it at all.

---

### Post by qwallis on 2008-07-03
After reading some other information I tried booting up the different kernel versions available in my boot menu, Going back all the way to 2.6.24-14 cured the problem (but I did balls up my screen resolution for a while): wireless doesn't work with the rest of the kernel versions I can choose from up to 2.6.24-19

I have tried removing the connection details and making a new wireless connection but that didn't work either.

---

### Post by qwallis on 2008-07-03
Well I didn't solve this problem exactly, instead I purchased a Linux compatible WiFi card. I figured that I would need another one anyway, because the old computer which will stay at home is ugly as hell, so will probably be confined to the bedroom, so I will use the old USB stick with 7.10 and **not** upgrade to 8.04
The new network card works like a dream and I even have signal strength showing, which never worked with the USB stick.

I'll mark the thread as solved, although the problem itself wasn't. Hopefully the other people will find a way round it, as I'll need it if I ever forget and click the upgrade button!

---

