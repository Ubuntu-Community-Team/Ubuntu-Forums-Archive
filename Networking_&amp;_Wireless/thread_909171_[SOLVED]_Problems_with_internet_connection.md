---
title: "[SOLVED] Problems with internet connection"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by pratekin on 2008-09-03
I just bought a dell precesion m2400 laptop and want to dual boot Vista with Ubuntu 8.04.  When I loaded the live cd, it did not recognize my network cards, so I can't get on the internet.  I went ahead and installed it so that I can work on it, but I am having problems figuring out what to do to get the networking up and running.  I have had problems in the past with wireless, but never with my wired connection.  I am also having problems with the nvidia card, but I am sure I can fix that once I get the internet up and working.  Any help would be much appreciated.  Thank you.

---

### Post by falcon61102 on 2008-09-03
Alright, well we need a little info about your hardware to be able to help you out.  Could you open up a terminal, run and post the results of the following command:
```
sudo lshw -C network
```

If you can't get online with that computer, you can copy the results into a text file either save it on a USB drive or shared space between Vista and Ubuntu so that you can post it hear.

And yeah, once you get the network stuff up, it should be easy to fix your video card trouble.

---

### Post by pratekin on 2008-09-03
Sorry it took so long to post again.  I did some research and found out that the kernel that I am using does not play nice with my ethernet card.  Without that, I can't use the usual means to fix my wireless card (i.e.-ndiswrapper, etc.).  I saw that the alpha 5 version of ibex will be released tomorrow and the new kernel is included with the iso and should fix my ethernet card, which should allow me to fix all the rest.  If that doesn't work, I will post some outputs and go from there.  Thanks for all who have helped.

---

### Post by falcon61102 on 2008-09-03
No worries and good luck with that.

---

### Post by pratekin on 2008-09-04
Started out this morning with loading the live cd with alpha 4 version of ibex.  Everything seems to work but the wireless, but that is an easy fix.  So I guess I will just stay with alpha until it is released.  Not a big deal because worst case is I just boot back into vista if I really need to.  Thanks for everyone's help.

---

### Post by gfeijoo on 2009-01-26
Hi pratekin,

I am wondering if installing Ubuntu 8.10 solved all the problems for you. I bounght a Dell M2400 and am having the same problems: ethernet and wireless card are not working.

Thank you,

Gonzalo

---

