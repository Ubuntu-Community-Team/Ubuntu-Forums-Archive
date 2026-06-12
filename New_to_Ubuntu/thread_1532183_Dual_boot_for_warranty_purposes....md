---
title: "Dual boot for warranty purposes..."
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Mike Krall on 2010-07-16
I've a new Win 7 laptop with a free two year warranty coming to run Ubuntu 10.04. I was told by the seller their tech support would need to work in Windows to do diagnostic checks, etc. if there were hardware/software problems... that they couldn't/wouldn't work through a non-Windows OS. 

Given that, I've been reading dual-boot threads here, on psycocats, and others. It dawned on me I might be able to deal with hardware diagnostic though Ubuntu if I can translate for the Window-head-Tech's needs. 

Is it even possible? Is it reasonably "Absolute *Real* Beginner" possible? 

Mike

---

### Post by SnickerSnack on 2010-07-16
> **Mike Krall said:**
> I've a new Win 7 laptop with a free two year warranty coming to run Ubuntu 10.04. I was told by the seller their tech support would need to work in Windows to do diagnostic checks, etc. if there were hardware/software problems... that they couldn't/wouldn't work through a non-Windows OS. 

Given that, I've been reading dual-boot threads here, on pycocats, and others. It dawned on me I might be able to deal with hardware diagnostic though Ubuntu if I can translate for the Window-head-Tech's needs. 

Is it even possible? Is it reasonably "Absolute *Real* Beginner" possible? 

Mike

I doubt it.  If they get even a hint that you're not using windows, they probably won't help you.

I'd recommend resizing the windows partition to only the minimum needed, and then dual booting with ubuntu.  Be warned, resizing will probably damage the windows install, and you'll probably have to reinstall it (in the new, smaller space).

---

### Post by indytim on 2010-07-16
If you re-size windows 7 **from within Windows 7** you should probably be good-to-go for the dual boot.

-IndyTim / DataMan

---

### Post by Gone fishing on 2010-07-16
> Be warned, resizing will probably damage the windows install, and you'll probably have to reinstall it (in the new, smaller space). 

I've never had a problem when resizing windows other than having to run chkdisk sometimes. I'd say probably not - it would probably be a good idea to defrag Windows before partitioning

---

### Post by SnickerSnack on 2010-07-16
> **Gone fishing said:**
> I've never had a problem when resizing windows other than having to run chkdisk sometimes. I'd say probably not - it would probably be a good idea to defrag Windows before partitioning

I should have said "possibly", rather than probably.  I've had problems with partition despite following guides.

---

### Post by cetoka on 2010-07-16
Last month the hard drive failed and I had the same problem.The place  where I had bought the PC told me that I had to have Windows installed  so that they can make diagnostic tests on Windows.Unfortunately the new  hard disk failed again and I had to shrink windows and install Ubuntu a  couple of times.
The only program I used to change partitions (shrink windows partition)  is Easeus Partition Master home edition and it never let me down.Evey  time I had problem with my desktop the service installed Windows on the  whole hard disk and I shrunk it using Easeus.
Now I have windows on the first partition (for the need of the service)  and Ubuntu as my main operating system.
Everytime before using Easeus I defragged the system with Puran defrag free.It worked for me more than 4 times.

---

### Post by mastablasta on 2010-07-16
Dual booting is easilly don (especially if Windows are alreaady installed). However you MUST do defraging (can be done with windows default defrager) and after defragging it is also necessary to permorm full checkdisk (CHKDSK /r). This might take a while since you iwll also be recovering and marking any bad secotrs. after these two things are done you can easilly shrink win parition and create separate Ubuntu partition during ubuntu install.

---

### Post by Mark Phelps on 2010-07-16
If you're dual-booting so you can teach techs how to do MS Windows diags using Linux, you're completely wasting your time.

Also, in terms of warranty support, the seller gets to decide the warranty terms, not the buyer, and in these cases, providers of pre-installed systems are very touchy about anyone making substantial changes.  Meaning, it's very likely that installing a different OS will void any support warranty you have.

---

### Post by Mike Krall on 2010-07-16
Thank you all...

***mastablasta***...  I've seen it as "chkdsk /r.  Is it that, or all caps., or either?

***Mark***... No, not looking to "teach".  I bought the Asus at XoticPC and asked them about warranty with only Ubuntu and Win 7/Ubuntu. For them it's a question of techs not knowing Ubuntu to be able to help... not a warranty breaker. 

Mike

---

### Post by LowSky on 2010-07-16
I forgot where I read it but a recent article stated most Computer Warranties from OEMs like Dell, HP, Acer, and Apple are worthless.

---

### Post by Mike Krall on 2010-07-16
> **SnickerSnack said:**
> I'd recommend resizing the windows partition to only the minimum needed, and then dual booting with ubuntu.

What is minimum size for Windows 7 Home Premium 64-Bit in a dual boot partition?

Mike

---

### Post by sailorboy on 2010-07-18
I wouldn't go under 20g but thats a guess, I have always allowed the default half split that's offered on a dual boot.

---

### Post by gunfyter on 2010-07-18
Why would you need to Partition the drive?  Can't just use WUBI?

---

### Post by Mike Krall on 2010-07-18
> **gunfyter said:**
> Why would you need to Partition the drive?  Can't just use WUBI?

The only reason I'm going to have Win 7 Home Premium 64bit on the machine at all is to use if there are warranty things needing to use it for diagnosing. 

I should have said that in my last post... I want to stuff Win 7 into smallest reasonable area and wait for the warranty to expire... then out the door it goes. 

Between posting the question and now, I knocked around the "dual boot" threads and came to understand 20GB min. (like "sailerboy" said), 30GB better, and maybe 40GB just to be absolutely sure. 

The HDD on the Asus coming tomorrow is 320GB so giving up 30-40 will be easy.

---

### Post by sprocket10 on 2010-07-18
Mike,

I'd give Win7 ~ 40GB for plenty of room. Install, then use windows 7 built in partition resizing tool to get it adjusted. Very easy to do. I didn't have to defrag when I did the resizing on my machine.

Are you saying that the asus hardware warranty depends on having windows installed? Because, if you don't care about using windows at all, you may as well not install it and not have to get windows tech support (which is probably garbage anyway). Win-win ;) 

Good luck!

---

### Post by S.R on 2010-07-18
The min for Win7 is 16 GB available hard disk space (32-bit) or 20 GB (64-bit).

If you defrag your windows partition before resizing your odds of data loss become manageable.

---

### Post by Mike Krall on 2010-07-20
> **sprocket10 said:**
> Mike,

Are you saying that the asus hardware warranty depends on having windows installed? Because, if you don't care about using windows at all, you may as well not install it and not have to get windows tech support (which is probably garbage anyway). Win-win ;) 

Good luck!

I talked with XoticPC awhile about warranty conditions on the Asus. They felt tech support would not be able to work in Ubuntu. If I need tech support for internal diagnostics, Win 7 needs to be available, was their opinion.

Mike

---

### Post by Mike Krall on 2010-07-20
> **gunfyter said:**
> Why would you need to Partition the drive?  Can't just use WUBI?
I know little about Wubi but I'll look into it. Came across Psycocats' write up on it. On the front of it, it seems like I could live with it... boot to Ubuntu... leave Windows in it's little closet and do a clean Ubuntu install at warranty end. 

Mike

---

### Post by M1ke on 2010-07-20
> **Mike Krall said:**
> I know little about Wubi but I'll look into it. Came across Psycocats' write up on it. On the front of it, it seems like I could live with it... boot to Ubuntu... leave Windows in it's little closet and do a clean Ubuntu install at warranty end. 
 
Mike
 
If the sole purpose of your Windows installation is to keep within the terms of the warranty or make life easier getting tech support, I wouldn't bother with wubi. Set up a proper dual-boot per the guidelines scattered about this forum (it's pretty simple - it was one of the very first things as I did as a linux newcomer and I had no problems!) and you'll have the peace of mind you're looking for. Ubuntu for your computing, Windows 7 intact should something go bang and you end up relying on the tech support people for help.
 
That said, the membership here is pretty knowledgeable so should you develop hardware trouble it's entirely likely you'll be able to diagnose it yourself via Ubuntu with help from people here :)

---

### Post by Mike Krall on 2010-07-20
> **M1ke said:**
> If the sole purpose of your Windows installation is to keep within the terms of the warranty or make life easier getting tech support, I wouldn't bother with wubi. Set up a proper dual-boot per the guidelines scattered about this forum...
 
...the membership here is pretty knowledgeable so should you develop hardware trouble it's entirely likely you'll be able to diagnose it yourself via Ubuntu with help from people here :)

I get it... I'd prefer a dual boot, given the need to keep Windows but not use it.

I understand a lot of help is available but I think what XoticPC/Asus told me is... verification of faulty hardware has to happen prior to warranty service... Windows OS being the way "they" would do that.

Do I miss understand?

Mike

M1ke... does the link in your signature have dual-booting info?

---

### Post by M1ke on 2010-07-20
> **Mike Krall said:**
> I understand a lot of help is available but I think what XoticPC/Asus told me is... verification of faulty hardware has to happen prior to warranty service... Windows OS being the way "they" would do that.
 
Yeah, that's the impression I got from your posts and it stands to reason. It's complicated (and expensive) for a company to offer tech support for a variety of hardware and across multiple OS'!
 
> **Mike Krall said:**
> M1ke... does the link in your signature have dual-booting info?
 
Unfortunately not, but I found excellent step-by-step guidelines on this forum with a quick search when I was getting set up. In a nutshell, you:
[LIST]
[*]Boot in to Windows, defragment (to be safe) and then use its own drive management tools to "shrink" the partition to whatever size you'd like. This'll leave you with a large "unallocated" space on the disk to install Ubuntu
[*]Restart Windows once or twice to give it a chance to reorganise its files for the new, shrunken partition size. Some advise running a disk check here to make sure all is well, but I don't think I did as I had very little data there anyway
[*]Shut down Windows and boot from your Ubuntu CD/USB stick and install as normal, remembering to specify your partitions manually or tell it to install alongside Windows
[/LIST]It's not as complicated as it sounds!

---

### Post by Mike Krall on 2010-07-20
> **M1ke said:**
> ...I found excellent step-by-step guidelines on this forum with a quick search when I was getting set up. In a nutshell, you:
[LIST]
[*]Boot in to Windows, defragment (to be safe) and then use its own drive management tools to "shrink" the partition to whatever size you'd like. This'll leave you with a large "unallocated" space on the disk to install Ubuntu
[*]Restart Windows once or twice to give it a chance to reorganise its files for the new, shrunken partition size. Some advise running a disk check here to make sure all is well, but I don't think I did as I had very little data there anyway
[*]Shut down Windows and boot from your Ubuntu CD/USB stick and install as normal, remembering to specify your partitions manually or tell it to install alongside Windows
[/LIST]It's not as complicated as it sounds!

M1ke,

That's a good rough outline. I'm going to format it in a document as step headings, print it out an use it for a process sheet... thanks!

I've messed with this before about 3 years ago... put 6.06 into an already old Sager after dumping Windows XP... and I spent the time waiting for the new computer (Asus UL50AG-RSTBK03) reading "dual boot partitioning" threads.

I suppose, I ought to call this "SOLVED" and start another thread... I've got some questions that maybe ought to be separated out from this one.

Thank you, all...

Mike

---

