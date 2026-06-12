---
title: "upgrade problem.. need advice"
date: 2009-11-18
forum: New to Ubuntu
---

### Post by 37452 on 2009-11-18
im using acer 5315 laptop n
i've just upgraded to karmic recently
but somehow the upgrade went wrong 
coz after the upgrade is finished n i reboot the pc
ubuntu can't recognize my sound hardware

?? is there any way to rooling back the upgrade so i can
get my jaunty version back n upgrade it in another time ??

or

?? is there any software that can list the software i'd install
in my pc n track the packet n save into another drive to install
it in later time ??
(i assume that when i use synaptic or apt-get command, the system
download the packet of a software is same 
like when i do the manual installation)
so the raw packet of the software is somewhere in the '/' which i didn't know

any suggestion will be appreciated
n sorry if my english is bad :P

---

### Post by masux594 on 2009-11-18
Unfortunately there's no way to rollback an upgrade of this kind.. So, if your only problem is the sound hw, u can feel lucky and i suggest to resolve the single problem.. if u have many problems, the only thing is to do a fresh install of the previous release [as i do =(]..

Sysc, A

P.s. If your sound doesen't work as well, it doesen't means that the upgrade went wrong, it means that the package that manage your sound has changed and maybe that these changes were used from your sound device..

---

### Post by diablo75 on 2009-11-18
There is a possibility the sound "not working" is actually the result of a bug fix.  Sometime ago, not too long, I encounterd a problem where, after a small upgrade, my sound stopped working.  After digging around I discovered a bug report filed for my card, and the solution to the bug was to swap the definition of a toggle for the digital sound out on the card.  So instead of it being enabled when the check box was unchecked, it would be enabled when it is checked.  The check was there, the digital out became enabled, and the analog out was disabled.  I went into the mixer on the upper panel and unchecked the box, and it solved the problem.

Can't promise that this is what you're encountering, but it's just an example of a small problem that can crop up that, given a little searching, can be solved quickly.

I'd start by doing a search for something like "Ubuntu 9.10 [name of sound card with model number here] stopped working after upgrade" using google.

---

