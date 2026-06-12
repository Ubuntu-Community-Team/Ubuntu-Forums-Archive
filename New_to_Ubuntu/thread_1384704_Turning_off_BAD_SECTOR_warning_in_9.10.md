---
title: "Turning off BAD SECTOR warning in 9.10"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-01-18
hi again,

I have a final issue with a Toshiba A205 which I have been setting up for 
a family member, with 9.10 AMD64.

All is great, except, when the machine boots up, I get the BAD SECTORS warning. Since this machine is for an everyday user who may freak out about it, or get 'help' from some well meaning person, I want it gone.

I have searched the forum and didn't see any threads on turning off the warning. Will google more and post back if I find something good, but wanted to start here since this forum has made Ubuntu really awesome.

peace,
wbg

---

### Post by Paqman on 2010-01-18
How many bad sectors have you actually got?

---

### Post by wannabegeek on 2010-01-18
when I ran gparted from the LiveCD, it didn't detect any bad sectors....
I think so at least, I got all green checks. Perhaps that's not the definitive test. 

I'm not sure I want to get the Toshiba software to 
do a more thorough job, although I might...I didn't see the Toshiba software on their site, which means I would have to call them...

Palimpsest says 67 bad sectors...

what do you think ?

wbg

---

### Post by warfacegod on 2010-01-18
As far as we have discovered he doesn't.

[http://ubuntuforums.org/showthread.php?t=1383792]("http://ubuntuforums.org/showthread.php?t=1383792")

---

### Post by wannabegeek on 2010-01-18
Since I can access gparted, doI need palimpsest ?

couldn't I remove it through   apt-get remove    ?

did some searching around on google, not sure that I can just 'remove'
palimpsest...

wbg

---

### Post by lavinog on 2010-01-18
The checks in gparted are for the filesystem, the checks in palimpset is done by the drives SMART system.

dont remove palimpset, you can disable the warning in palimpset or disable it through system>prefs>startup apps.  Uncheck Disk Notifications

edit: If you check the warning you can select "Don't warn me if this disk is failing"

---

### Post by agaray on 2010-01-18
Not sure if this is what you're looking for but, you can turn off disk notifications by unchecking it in System -- Preferences -- Startup Applications.

Andy

---

### Post by wannabegeek on 2010-01-18
Hey,

I checked the 'Don't tell me the disk failing' button, and that did what I wanted...I saw it before but hesitated, thinking 'what if it really is gonna fail ?'  I don't care at this point, the machine is for everyday non-business stuff. 

egalvan from an earlier thread sited above, had a good suggestion I didn't see right away, buy a used drive from an upgrade, from local repair shop. That's probably a modest expenditure...

I'll have to read about the differences b/w checking the file system and
the physical disk...thanks lavinog

I think this thread is done, unless someone wants to add some wisdom.

peace,
wbg

---

### Post by DougieFresh4U on 2010-01-18
Just a few days ago I was getting the 'bad sector' on my hard drive and there was an icon on the upper panel. When I clicked the icon a window opened and I checked the box that said 'do not show this again'

---

### Post by lavinog on 2010-01-18
I wouldn't worry about the warning so much.  My laptop has had that warning since karmic came out, and the issue most likely existed long before.  I use my laptop about 3hrs/day and no issues.

I had a desktop drive fail recently, the warning popped up right when it failed, so I would say if you get the warning, and your drive is still working, don't worry too much about it.

Hard drives are designed to have some bad sectors...nothing can be perfect.

---

### Post by presence1960 on 2010-01-18
> **lavinog said:**
> I wouldn't worry about the warning so much.  My laptop has had that warning since karmic came out, and the issue most likely existed long before.  I use my laptop about 3hrs/day and no issues.

I had a desktop drive fail recently, the warning popped up right when it failed, so I would say if you get the warning, and your drive is still working, don't worry too much about it.

Hard drives are designed to have some bad sectors...nothing can be perfect.

You can download a bootable utility from your hard disk manufacturer's web site that will check your disk and fix any errors that are fixable. I had the same thing happen after a power failure while my machine was running. palimpsest reported over 100 bad sectors. I downloaded the utility from seagate, burned it to CD and booted from it and it fixed all but one bad sector. That was over a month ago and that disk's status has not changed as I am keeping an eye on it.

---

### Post by warfacegod on 2010-01-19
Palimpset is still having issues with false positives. I look at mine every few days. Sometimes the SMART status is bad, sometimes not.

---

### Post by presence1960 on 2010-01-19
> **warfacegod said:**
> Palimpset is still having issues with false positives. I look at mine every few days. Sometimes the SMART status is bad, sometimes not.

That's why I doublecheck with gsmartcontrol and the Seagate utility. Those 2 are consistently the same.

---

### Post by warfacegod on 2010-01-19
> **presence1960 said:**
> That's why I doublecheck with gsmartcontrol and the Seagate utility. Those 2 are consistently the same.

Does gsmartcontrol install with a GUI?

---

### Post by warfacegod on 2010-01-19
Scratch that last post I just installed it. Looks like a highly useful tool.

---

