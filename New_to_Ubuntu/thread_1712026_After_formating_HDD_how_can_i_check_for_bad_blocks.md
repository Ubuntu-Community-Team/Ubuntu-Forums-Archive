---
title: "After formating HDD how can i check for bad blocks?"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by hopelessone on 2011-03-22
Hi,

2TB WD Caviar Green...having trouble with it so i'm moving all the files off using:
```
sudo dd_rescue /dev/sdc1 /mnt/hdd_1/backup.img
```
I will format sdc1 to ext4
So my question is:
How can i do a check of the whole hard drive to record any bad blocks after formatting it?
So far i got:
```
e2fsck -ycC /dev/sda1
```
is that OK?
Many Thanks..

---

### Post by Dutch70 on 2011-03-22
Will a SMARTData check from Disk Utility not give you what you're looking for? 

I know it will tell you if there are any bad sectors.

---

### Post by Paqman on 2011-03-22
Yep, check the SMART data for two things: reallocated bad sectors and sectors pending reallocation. The first is bad blocks that have been identified and removed from use, the second is bad blocks that haven't (and are therefor still a risk to your data).

Pretty much every drive will have a few reallocated sectors, that's fine. But if you have lots, or sectors that haven't been dealt with, then you have a problem.

---

### Post by hopelessone on 2011-03-22
Hey! Cool I forgot about that...

I got lots of error Reallocated Sector Count
How to fix this error?

---

### Post by Dutch70 on 2011-03-22
Whew, that's a lot of bad sectors. AFAIK, there is no way to fix it. It's a sign of pre-disk failure. It may last quite a while & it may not. From what I understand, that number is just going to grow. 

Paqman will know more about it though.

Best regards

*Edit: I've had 9 bad sectors on mine for about 6 months & it hasn't grown any.*

---

### Post by deconstrained on 2011-03-22
badblocks in non-destructive read/write mode (the -n flag), see man page for details.

I had a 2 TB drive die on me a little while ago (Samsung actually). It may not be that the surface got damaged or has bad sectors, but a problem the controller or mechanics are messed up (especially if filesystem checks tell you nothing is wrong with it). Countless butthurt reviewers on Newegg always howl about poor QC on 2TB drives, regardless of manufacturer, so maybe it's just that the size hasn't become mainstream enough yet.

Try the hard drive in the freezer trick, it worked for me, but that's only because I was meticulous with moisture control. I lined the bottom of a tupperware container with CaCl (the dehumidifier stuff you can get at a hardware store), covered that stuff with a cloth, put the hard drive on top of the cloth, sealed it and let it sit for a while before 24 hours in the cold to sap all the moisture out so that no condensation could take place.

Edit: I posted before you replied with the screenshot of that horrendous report of bad sectors... :-P

---

### Post by hopelessone on 2011-03-22
Hi I just checked others and 2 more have this error but less:
 Can you give a coding example of how to fix this?
Thanks guys..

---

### Post by Dutch70 on 2011-03-22
> **hopelessone said:**
> Hi I just checked others and 2 more have this error but less:
 Can you give a coding example of how to fix this?
Thanks guys..

```
cd office-depot
sudo apt-get new-disk
```


Sorry :) ...I couldn't resist. 

As I said earlier though, I don't think it's something you can fix. I'd back up my important info & be prepared for it to fail, even though it may not do so for a while. 

On a more positive note though, I kind of freaked out when I first saw that mine had 9 bad sectors. That was about 6 months ago. The only problem I've had with it is I can't shrink windows down anymore than it already is.

Maybe someone else will have more & positive info for us both.

---

### Post by yopnono on 2011-03-22
Hum that's funny. On ubuntu smart a get sector error on all disk I have tried. Old as new ones.

---

### Post by Dutch70 on 2011-03-22
It looks like the hdd with 1275 bad sectors is less than a year old, it should still be under warranty. Sometimes the warranty on hdd's is quite a long time, so you're other ones may be as well. Certainly worth checking on.

---

### Post by Paqman on 2011-03-22
> **Dutch70 said:**
> 
Paqman will know more about it though.


Nope, sounds like you've got it covered, everything below is good advice.

> **Dutch70 said:**
> I'd back up my important info & be prepared for it to fail, even though it may not do so for a while. 


> **Dutch70 said:**
> It looks like the hdd with 1275 bad sectors is less than a year old, it should still be under warranty. Sometimes the warranty on hdd's is quite a long time, so you're other ones may be as well. Certainly worth checking on.

---

### Post by hopelessone on 2011-03-22
I checked WD website and entered the serial number and its still under warranty...great news...thanks guys...

---

### Post by Dutch70 on 2011-03-22
> **hopelessone said:**
> I checked WD website and entered the serial number and its still under warranty...great news...thanks guys...

Great! Glad to hear that :D

ps. Since that is true, don't use the code I gave you earlier ;)

---

