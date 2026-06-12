---
title: "Trouble uninstalling / removing a broken package"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by _DeepBlue on 2010-09-29
First off i'm really new to this, and i'm not really the fastest of learners... i'm still using karmic because i am unable to install updates or anything. 

I cant download updates or anything because of two broken packages, "bsd-mailx" and "lsb-core".

if I try to use synaptic to uninstall or remove or do anything with these packages, i get the following error message: 

> E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
unfortunately i have no idea what that means..

i've had a look on google, and seen some similar problems, but im not confident enough to try some solutions that might end up worsening my situation... and i'd like to actually understand what i'm doing... any help would be greatly appreciated! :)

---

### Post by emoguitarist06 on 2010-09-29
I'm no pro either but I want to say that it's trying to say another packagemanager or synaptic is open. Just restart your computer and don't open anything up except synaptic and try again

---

### Post by Paqman on 2010-09-29
You can only have one package management app open at a time. So that means only one of Synaptic, Ubuntu Software Centre, Update Manager, Gdebi, or apt-get on the command line. If you're sure that you don't have two of these open at once, then close Synaptic and delete that lock file if it's still there. When you re-open Synaptic you should be able to fix those two broken packages.

---

### Post by _DeepBlue on 2010-09-29
Wow, fantastic! it was as easy as that, all i had to do was reboot! Thanks very much emoguitarist! 

thanks for the replies guys! 

:):)

---

