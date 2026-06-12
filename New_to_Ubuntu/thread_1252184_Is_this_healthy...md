---
title: "Is this healthy?.."
date: 2009-08-28
forum: New to Ubuntu
---

### Post by balaji_9r on 2009-08-28
HI, i am a new user... i keep switching the hard drive on my dell inspiron 1300,,, b/n two 
one with UBUNTU and the second one with WINDOWS. .. does this affect the health of my laptop?.... things that went bad...when i did this...
1---> my Ctrl button does not work in any of the O.S
2---> my system clock will not sync in windows automatically, even if i try to update my time online... i had to manually adjust it....I AM YET TO VERIFY THE BIOS TIME..

CAN SOMEONE PLS EDUCATE ME ON THIS ....



NOTE: I AM AWARE OF DUEL BOOTING..I GOT MY REASON AS TO WHY I DO NOT WANT THAT...

---

### Post by QIII on 2009-08-28
If your Control key does not work in either OS, then you have pretty well eliminated software as a culprit.  That points to hardware.

As for the clock setting in Windows...  Is the difference one of a minute or two, or is it hours (as in UTC)?

---

### Post by balaji_9r on 2009-08-28
it was more than 4  to 5 hours... untill i manually adjusted it yesterday....i do not understand (UTC)?????..

---

### Post by LowSky on 2009-08-28
Fix the BIOS time, and things will be fine.

CTRL not working, try a new keyboard, off newegg/ebay for about $10

switching hard drives will not be an issue with health. Worse thing you could do is ruin the connectors from mishandling the removal/installation...

---

### Post by balaji_9r on 2009-08-28
thank you... it is a laptop.. i got 5 keyboards in the house...lol....but it is good to know that nothing wrong in switching hard drives...
another question... my laptop heats up really fast with windows...but takes a while or never really gets that hot when i use ubuntu... it that normal...

---

### Post by QIII on 2009-08-28
Sounds like a UTC issue (the number of time zones you are away from Greenwich, England) and your Ubuntu disk is using GMT.

From the terminal in Ubuntu, 

```
 gksudo gedit /etc/default/rcS
```(If you are using Kubuntu, change gksudo to kdesu)

Change the line 

```
UTC=yes
```to 

```
UTC=no
```
Changing disks is probably doing what would effectively be happening in a dual boot configuration when UTC is set to yes in Ubuntu.

Edit:  Sorry.  UTC is coordinated universal time.[COLOR=#ff0000][/COLOR]

---

### Post by balaji_9r on 2009-08-31
thank you Mr.QIII.... that was very helpful and it made more sense...
the thing is ubuntu updates the time and date automatically but windows does not ... any particular reasons... (i try to update my date and time using auto update in windows and it will not work). ..
and where can i learn about the codes the ones..u just suggested me.. pls let me know.. i would like to learn. thank you again

---

### Post by hockeytux on 2009-08-31
> **balaji_9r said:**
> it was more than 4  to 5 hours... untill i manually adjusted it yesterday....i do not understand (UTC)?????..

UTC/GMT is actually UK time in winter-only. Right now its an hour less.

---

