---
title: "RutilT To Sender!"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by sulligogs on 2007-09-04
Hi Everyone

I have two PCs with Ubuntu Feisty Fawn on.  They are an AMD XP 2200+ and an AMD 750mhz Duron.  Each use an Edimax EW-7128g wireless card that use the RT61 (or maybe RT2561?) chipset.

Anyway, when I first installed Ubuntu anywhere between 2 seconds to 2 days I would get a severe lockup on the desktop.  Pulling my hair left, right and center wouldn't help then I finally traced the problem to the RT61 modules.  Surely, after blacklisting them, the problem would vanish.

Anyway, I was quite content to use my laptop which also had Ubuntu installed with an Edimax EW-7108PCg PC card, based on the RT2560 chipset.  That ran without problems.

Then one day I eventually tried [RutilT]("http://cbbk.free.fr/bonrom/") and lo and behold it fixed everything!  Even though it's supposed to only be a "helper" for your wireless card.  Whatever it does differently it's fixed everything!  My two machines run like a couple of cats purring after a tin of sardines.

I wasn't able to build it myself from the installation, as I was still a bit of a noob, but I found this:-

[http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb]("http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/rutilt_0.14-0~3v1ubuntu1_i386.deb") 

which essentially installs from the desktop without any complaints.  Eventually, I understood the requirements to build the latest version of RutilT and now I am happily running v0.15.  With this one you can compile it with "--launcher=nopasswd" and you won't even need to give the administrative password in order for it to run.  Magic!

I love the way how you can specify it to load on startup just by going to System->Preferences->Sessions.  And with it you can give a default wireless profile just by using "rutilt -tp <PROFILE>".  This software, along with avoiding the password and having it start automatically has made my Ubuntu experience a 10/10.

I wish to thank the RutilT authors for their brilliant efforts.  They may have very nearly saved me from going back to Windows.  I hope this helps anybody else with their wireless woes.

Sulligogs

---

### Post by kevdog on 2007-09-04
Ive compiled this already, however as a gift to the ubuntu community, why dont you write up the steps you did to compile the rutilt utility and publish it here in the forums.  It would be a welcome addition.  In addition you have a rt61 chipset (not whatever you have listed).

---

