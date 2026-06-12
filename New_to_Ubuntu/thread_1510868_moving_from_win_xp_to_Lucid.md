---
title: "moving from win xp to Lucid"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by mikelspencr on 2010-06-16
ok, my name is Mikel, and i've been using ubuntu on my laptop for about a month...

im moving my win computer to Lucid now, an im actually posting this from the usb boot of lucid, so i know it works perfectly lol.

ok, here's my problem: i am willing to delete everything from my 2 hdd's ( a 40 gb and a 30 gb, hda and hdb, respectively) and have ubuntu control the whole computer. how would i go about reformatting, partitioning, etc in order to make use of both hard drives? 

im not sure exactly if this is the best way to describe my issue, but i can explain better if needed. 

simply put: wipe windows from both drives, install linux and be able to access both drives with no problems


TY!

---

### Post by joshmuffin on 2010-06-16
Just install it like normal when you get to partitioning step give ubuntu 100% really you should make a swap partition aswell but save that for another thread

I have only updated to lucid but on the old disks the option was "Guided - use whole disk"

---

### Post by mikelspencr on 2010-06-16
yeah, I thought about using that method, but I was unsure whether I would need to install lucid on BOTH hard drives, or if I could install it on one and then format the second. Does this sound about right to you? Btw... Thanks for the fast reply!

EDIT: I would have no problem doing a swap partition, if you don't mind telling me the basics if doin it. I have some experience in linux now, so I feel capable. I just want to get this set up so that I can save on stress later

---

### Post by realzippy on 2010-06-16
If you do not choose *manual* during install/partitioning,ubuntu will create a swap partition automatically.
BTW,with 2 discs you can run a software RAID0/1...

---

### Post by mikelspencr on 2010-06-16
ok. I'll give it a shot once I get the hance. I'll let you know how it goes, and if it works perfectly, I'll mark this  SOLVED BUT UNTIL THEN, MORE REPLIES PLEASE LOL

---

### Post by mbzn on 2010-06-16
Depending on how much space you'll need i would suggest
sda1 8GiB on / (will give you lots of space for whatever you install)
sda2 32GiB on /home
sdb1 4GiB swap area
sdb2 26Gib as storage (for music or whatever you have allot of)

I assumed you have SATA drives, so the / and swap on different drives could give you a slight (probably unnoticeable) speed increase.

---

### Post by mikelspencr on 2010-06-16
i guess i did forget, but i am on an (obviously outdated) IDE setup

---

### Post by realzippy on 2010-06-16
Suggest you plug in only 1 disc and install Lucid with the *use full disc option.*Creating/changing partitions can be done afterwards easily.
Your IDE Hardware will run.Will be called *hda* instead of *sda*.

---

### Post by mikelspencr on 2010-06-17
much appreciated guys. I'll be doing the install once I get home. Will update afterwards. Final question, I promise lol. 

will saving any packages between separate hdd's cause any problems? I'm sure that there is the dependacy issue assuming I take out a drive or god forbid one fails. Other than that, ( I'm asking simply in case I NEED to do it for any reason) will it cause a problem?

---

### Post by WinterRain on 2010-06-17
Ubuntu will only install on one drive, so no, there will be no problems. You can use the other drive for storage if you wish.

---

### Post by mastablasta on 2010-06-17
> **WinterRain said:**
> Ubuntu will only install on one drive, so no, there will be no problems. You can use the other drive for storage if you wish.
 
 
Yes and that is because usually on desktops only one disk is set as master disk (primary) while the other one will likely be slave (secondary). and by default operating systems like to install on primary. you will see the other one later in "Places" menu.

---

### Post by mikelspencr on 2010-06-18
ok awesome info. Thanks... Now lol. I can't get the usb to boot again on my desktop. I tested it on my laptop and it's just fine... But when I plug it into my desktopm I have it set to load from usb first, but the windows section starts up again... Any ideas?

---

