---
title: "Hoping for help..."
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by jmitche1 on 2008-10-31
I have an hp dv200 laptop with a broadcom bcm4310 wireless card. I am running the news version of ubuntu and can't use my wireless internet. After doing some research I am guessing that this is one of the unsupported wireless cards. 

I am sorry for being such a noob. This is my first time running ubuntu or linux for that matter. I have about had it with windows and wanted to try something different. I am also sorry if this question has been asked before but from the other threads I am unable to understand. Any help would be greatly appreciated and I thank you all in advanced! :)

---

### Post by vitorgatti on 2008-10-31
[http://www.google.com.br/search?hl=pt-BR&q=bcm4310+ubuntu&btnG=Pesquisa+Google&meta=](http://www.google.com.br/search?hl=pt-BR&q=bcm4310+ubuntu&btnG=Pesquisa+Google&meta=)

A lot of stuff showed up with this simple search on Google.
Welcome to Linux and don't give up! Some stuff you will have to research and install things manually, but most of the time you will see that Linux is a lot better than Windows!

Good luck

---

### Post by eternal_sage on 2008-10-31
[http://ubuntuforums.org/showthread.php?t=963978](http://ubuntuforums.org/showthread.php?t=963978)

this thread may give you some help. it has some, and others not yet, but help is making its way around.

and as a fellow noob, (been at it about 7 months now) i can tell you for certain that its worth the effort now. once its working, you are in the green. laptops are the hardest to get working, but are well worth the effort if you can do it.

welcome to the gang!

---

### Post by Ayuthia on 2008-10-31
> **jmitche1 said:**
> I have an hp dv200 laptop with a broadcom bcm4310 wireless card. I am running the news version of ubuntu and can't use my wireless internet. After doing some research I am guessing that this is one of the unsupported wireless cards. 

I am sorry for being such a noob. This is my first time running ubuntu or linux for that matter. I have about had it with windows and wanted to try something different. I am also sorry if this question has been asked before but from the other threads I am unable to understand. Any help would be greatly appreciated and I thank you all in advanced! :)

This card is supported in 8.04.1 (Hardy) and Intrepid.  The card will be correctly listed as the bcm4312 (14e4:4315).  This card uses the wl driver (Broadcom STA).  It should work as soon as you activate the driver in System->Administration->Hardware Drivers.  However in Intrepid, you might encounter a bug that will cause it to not work instantly.  If that happens, you will need to go into the Terminal and type:
```
sudo modprobe -r b43 ssb wl
sudo modprobe ieee80211_crypt_tkip
sudo modprobe wl
sudo /etc/init.d/networking restart
```

---

