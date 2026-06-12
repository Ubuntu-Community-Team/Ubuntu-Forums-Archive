---
title: "Internet help for a noob, please!"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by NukeLuke on 2008-12-20
Ok, so i just got a new dell, but since the pre-loaded systems they were selling lacked a wirless card, i decided to get a regular Inspirion 530, lo and behold Broadcom screwed me!
i cannot get my wireless to work. and to make matters worse, ive messed around in terminal so much that i think i&#7743; really screwed:
i changed a bunch of settings.
i ran bcm43xxx-fwcutter, and it&#347; still not working
and i finally just plugged it to a hardwired connection, and got fwcutter to work, but nothing

HELLLLLLLLLLLLLLLLP!!!!

:P

---

### Post by Zeedok on 2008-12-20
First thing to check is that your wireless card is compatible.  [Check this wiki page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported").

I have fiddled around with ndiswrapper and a wireless USB dongle heaps without luck in the past.  Eventually I tracked down a wireless card that was listed as "works out of the box", and it worked perfectly.  Th.e best $40 I ever spent.

Good luck.

---

### Post by NukeLuke on 2008-12-20
HAHAHA, somehow, when i got all my updates after hardwiring in, there was a boradcom driver just waiting for me- dont know if it was fwcutter or what, but noww i&#7743; up and running!!!
(of course, now i have to figure out how to get rid of my abortive 2nd OS of ubuntu i interuppted the partition of.
EXPLANATION:
i was getting so fed up i started installing a new version of ubuntu, i thought i had stopped it before it partitioned my dirve, but for some reason, i know have three OSes on my PC (ubuntu, the messed up Ubunut and Windows)
any help?

---

### Post by Iowan on 2008-12-20
Where does that aborted installation show up - bootup?  You can edit /boot/grub/menu.lst to remove the option.  If there is actually a partition set up for it (thought you said you aborted before this stage), that can probably be removed.

---

### Post by Zeedok on 2008-12-20
Install GParted from synaptic (if you haven't already).  Use this to work out which partition the "Messed-up Ubuntu" is on and you can reformat it, then expand your winXP or "Working Ubuntu" partitions to reclaim the space.  

BTW - are you seeing more than one entry for Ubuntu on your GRUB list (when you reboot)?  Is that what you mean when you say there is more than one Ubuntu?? Because, that's normal (there are a number of Linux Kernel headers that Ubuntu keeps)

---

### Post by NukeLuke on 2008-12-20
can't find Gparted in syn.
i know more than one is supposed to show, nowi'm getting doubles of all the ones i had before.
i'm pretty sure i stopped it before it actually partitioned.

---

