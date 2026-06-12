---
title: "HD Warning - Many Bad Sectors - &quot;Failure Imminent&quot;"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by jage on 2010-01-22
Unbuntu CD install is giving a warning about my laptop harddrive:
"Disk has many bad sectors"

I searched and most of what I saw on the disk warning posts seemed categorized "Don't worry about it", but also to look in Disk Utility for information about why the error is occurring.  I'm guessing the Don't worry about errors were probably for other types of errors...

I did look into Disk Utility and all the items but one look good.  Reallocated Sector Count was a warning and Disk Utility is saying I need to replace the HD, disk failure is imminent.

Screenshots are attached.  Any chance it's not that bad?

Question is, is it possible to salvage the drive by formatting, or should I have already ordered its replacement?

---

### Post by NCLI on 2010-01-22
Bad sectors means that there's something physically wrong with the drive, more specifically that parts o it are in such a bad shape that they can't be read. If I were you, I'd backup everything you have on the drive ASAP and order a new one.

You're lucky you tried the livecd and found out about this before it was too late ;)

---

### Post by pricetech on 2010-01-22
To be certain, download and run the diags from your system manufacturer or the drive manufacturer.

Drives are pretty reasonable though, so probably best not to even chance it.

---

### Post by JiuJitsu500 on 2010-01-22
Depends... age (writing/deleting files again and again) and messed up allocations (happens in file systems that write everything so close together... see: fragmenting) can cause bad sectors and happens in ALL file systems... but journaling type is much harder because of the way things are stored... still though once a drive is like 80% full or more it can get crazy.

Also, bumping the hard drive while it's on can too... a disc spinning at 5400 to 7200 rpm is not that hard to mess up by a simple knock.

Luckily, the first described is a software type bad sector ("soft" bad sector) and reformatting or deleting usually does the trick, and if you plan on a clean install of something, will fix the problem.

Hardware ("hard" or mechanical) bad sectors are not correctable by any software or conventional means.

So more than likely, it's just a sign of age and isn't much to worry about if you reformat it... my year old (not even) 500GB says it too (disc utility) and it's working as fast and well as it did when I first opened it. But, if you'd like, and you have the time, re-formatting wouldn't hurt unless you can't back the drive up...

---

### Post by jage on 2010-01-22
Everything is backed up, there is actually very little used on the drive except Windows and accompanying software.

So...if I format it and run/install Ubuntu, will the drive utility be able to tell on a fresh format, or do I need those manufacturer tools and/or to use it extensively again to bring up physical problems?

---

### Post by jbruced on 2010-01-22
If you're lucky, a reformat may make some sectors usable again, the only issue is, what caused the problem to begin with.

I's give it a shot, and start shopping for a cheap replacement.

My 2 cents.

---

### Post by JiuJitsu500 on 2010-01-22
A very well worth 2 cents :)

I'd try to reformat it if you don't care about what's on it... since you have everything backed up it won't be a problem but you will lose everything on that drive. Even partitions if you want to see if you can really get rid of the bad sectors since they're hard to individually locate (if even possible without the time).

If it's mechanical though, you did just waste a lot of time and effort... If it's a soft issue, and you really need this hard drive, it'll be worth it :) But seriously, save everything you don't want to lose somewhere off that drive, then do it...

But shooping for a cheap replacement is certainl never a bad idea when this type of thing happens :P

---

### Post by pricetech on 2010-01-23
I'd run the diags first.  While the install would be good experience even if the drive fails, so would running the diags.

Just a thought.

---

### Post by emarkay on 2010-01-24
I'd UNSOLVE this one - 2 new HDU's can NOT be bad!

Must investigate, but this is not normal...  One maybe, but another one, too?

160 GB ATA Fujitsu MHY2160BH, by the way...

---

### Post by valjes on 2010-01-24
I have the exact same thing some help would be nice.

---

### Post by emarkay on 2010-01-24
same issue here:
[http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2](http://georgia.ubuntuforums.org/showthread.php?t=1336267&page=2)

---

### Post by admiralspark on 2010-01-24
This is a common occurrence with Ubuntu 9.10, it has been known to show false positives on several machines. Please do a forum search to check for redundancy.

If it turns out you actually do have bad sectors, backup all valuable files and purchase a new HDD. I would use the HDD manufacturer's diagnostic software (90% of companies offer this to download for free) and run it through Windows to see if it's actually bad.

EDIT: I have a four year old, 7200rpm 100gb harddrive in my laptop, it's been used and abused (completely wiped and reformatted many MANY times) and it still runs fine, knock on wood. Unless you've purchased an off-brand HDD, you probably won't have severe damage.

---

### Post by warfacegod on 2010-01-24
Palimpset (Disk Utility) has been known to give false positives. gsmartcontrol is much better at giving reliable results and will give you more information to work with in diagnosing a problem.

```
sudo apt-get install gsmartcontrol
```

---

### Post by jage on 2010-01-25
E: Couldn't find package gsmartcontrol

First time I've tried to use apt-get... incidentally how do you paste to terminal?  Or better yet run xterm (or similar) for terminal windows?

Sorry I don't really understand apt-get... all the searches just say "It's so easy to use!", not actually HOW.  I tried it in ALT+F2 run application window and it did nothing then tried it in CRTL+ALT+F2 and it read list dependency and state and threw the above... Incidentally I haven't read the beginner's stickies yet.

Based on descriptions of the platter failing and dust creation with growing bad sectors, I ordered a Western Digitial 350 GB replacement anyway, but I've got two days to kill while it ships... maybe I should read the beginner's guides... :D

---

### Post by gnometorule on 2010-01-25
Check here for apt-get:

[http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html](http://www.ccl.net/cca/software/UNIX/updating-redhat/apt-howto/how-to-use-apt-get.html)

Basic commands: update, upgrade, dist-upgrade, install. Run them all by prefacing the entire command with 'sudo', then enter your password.

You start an xterm by typing...'xterm &'. :)

---

### Post by Paqman on 2010-01-25
> **jage said:**
> 
Sorry I don't really understand apt-get

Try Synaptic instead, it's a GUI for apt, and is excellent. System > Admin > Synaptic.

---

### Post by warfacegod on 2010-01-25
> **jage said:**
> E: Couldn't find package gsmartcontrol

First time I've tried to use apt-get... incidentally how do you paste to terminal?  Or better yet run xterm (or similar) for terminal windows?

Sorry I don't really understand apt-get... all the searches just say "It's so easy to use!", not actually HOW.  I tried it in ALT+F2 run application window and it did nothing then tried it in CRTL+ALT+F2 and it read list dependency and state and threw the above... Incidentally I haven't read the beginner's stickies yet.

Based on descriptions of the platter failing and dust creation with growing bad sectors, I ordered a Western Digitial 350 GB replacement anyway, but I've got two days to kill while it ships... maybe I should read the beginner's guides... :D

Copy and Paste in Terminal:

Shift+Ctrl+C or V

gsmartcontrol can also be found in Synaptic Package Manager.

---

### Post by jage on 2010-01-25
> **warfacegod said:**
> gsmartcontrol can also be found in Synaptic Package Manager.

Ahhhg.  I'm obviously missing something really basic.  Apt-get continues to give me the error and attached is a screenshot of where I THINK gsmartcontrol should be.

Sorry, just really confused.

---

### Post by eeeandrew on 2010-01-25
ok, lets make sure that your software database(repository) index is properly updated. I'll show how to do this in terminal its actually easier.

> sudo apt-get update 

to update the index and then run

> sudo apt-get install gsmartcontrol

Heres the ubuntu community wiki explaining how to use apt-get. I found it useful.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

Hope this helps.

---

### Post by warfacegod on 2010-01-25
You may need to make sure that "Multiverse" is enabled in Software Sources.

---

### Post by jage on 2010-01-25
> **warfacegod said:**
> You may need to make sure that "Multiverse" is enabled in Software Sources.

That worked.  Well it was actually checking "Universe" that got me gsmartcontrol.  For future readers make sure and close Synaptic Package Manager if you're going to use the GUI Software Sources... the conflict results in a check box without actually loading the SW sources (uncheck, recheck and close with Synaptic Package Manager closed to load).

---

### Post by warfacegod on 2010-01-25
> **jage said:**
> That worked.  Well it was actually checking "Universe" that got me gsmartcontrol.  For future readers make sure and close Synaptic Package Manager if you're going to use the GUI Software Sources... the conflict results in a check box without actually loading the SW sources (uncheck, recheck and close with Synaptic Package Manager closed to load).

Sorry, I should have mentioned the closing stuff part.

---

### Post by trooperchix on 2010-02-26
I have a brand new laptop, and I am getting this error.  I will say that I run Vista and installed Karmic on it as well.  How many folks are getting this error are also dual boot to Windows?  Could there be something at issue here?  Windows was installed first...

---

### Post by jage on 2010-02-27
I formatted the drive and installed Windows and Ubuntu again and it gave the same error.

I replaced the HD with a 350G Western Digital, installed WinXP again then Ubuntu again- and everything was fine.

I'm keeping the other drive around as it works for playing on, but I don't think it's a win/ubuntu conflict.

Good luck.

---

### Post by Mark Phelps on 2010-02-28
> **trooperchix said:**
> I have a brand new laptop, and I am getting this error.  I will say that I run Vista and installed Karmic on it as well.  How many folks are getting this error are also dual boot to Windows?  Could there be something at issue here?  Windows was installed first...

From the high numbers of posts from  folks who are getting these same warnings in 9.10, it's apparent that it is not strictly a dual-boot-with-MS-Windows problem.

At first , it looked like these were false positives -- but since then, there have been lots of posts from folks whose drives DID subsequently die.  So, there may be something to these errors after all.

Best advice I can give is to find out the manufacturer of your drive(s), go to their websites, and (presuming they offer it), download drive utilities from their sites and run them against your drives.  If THOSE utilities say your drives are error-free, you're getting false positives.

---

