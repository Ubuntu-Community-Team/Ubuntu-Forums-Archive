---
title: "Bad Sectors. Need help."
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Athomo on 2011-01-12
So my computer has 318 bad sectors. According to Smart Data in the Disk Utility. It only shows two when I click on Smart Data. I'll have screenshots posted on here with it. I'm not sure why my computer is like this. I've researched it, and I'm pretty sure it is because I partitioned my hard drive and ran Windows 7 Ultimate, and Ubuntu 10.04. I want to fix my computer. It is slowly going to hell. A while ago my computer came up with a message when it went through boot up. It said it was missing a kernel and to go to a website to fix it. I could never copy the website down fast enough before it would boot up. Now the only message it gives me is that the WMID is not detected. I have no clue how to fix it, and it would be greatly appreciated if someone could help me out. Thanks.

---

### Post by HereInOz on 2011-01-12
I would suggest that your hard disk is gradually shuffling off its mortal coil and going to meet its maker.  

I could be wrong but growing bad sectors, boot errors and such, plus the information contained in the images you posted, usually indicates a dying HDD, and you need to take steps to backup your data and plan a HDD replacement.

---

### Post by Athomo on 2011-01-12
Is there any way I can try and fix it? It would be a great help if you or anyone else could.

---

### Post by dFlyer on 2011-01-12
I would recommend you back up your important data and replace your hard drive as soon a possible.

---

### Post by judedawson on 2011-01-12
Hi Athomo,

How old is the hard disk?

From,
Jude

---

### Post by Paqman on 2011-01-12
> **Athomo said:**
> Is there any way I can try and fix it? It would be a great help if you or anyone else could.

No, it's dying. Back up your data right now.

---

### Post by matt_symes on 2011-01-12
Hi

Can it be fixed ? No, those sectors are damaged and that is a hardware error. Back up your data. You may wait to see if the count rises but the best best, i think, is to purchase a new drive.

This might give some in site.

[http://www.hdsentinel.com/smart/index.php](http://www.hdsentinel.com/smart/index.php)

Kind regards

---

### Post by bodhi.zazen on 2011-01-12
Bad sectors are normal wear and tear, they will increase until the HD fails, and they can not be repaired.

There are hard ware solutions - ie the disk drive no longer uses these sectors - and software solutions - ie repairing the file system and restoring from backup.

Keep using the HD until it is a problem.

You should have backups of your important data off the hard drive no matter the number of bad sectors.

---

### Post by Paqman on 2011-01-13
> **bodhi.zazen said:**
> 
Keep using the HD until it is a problem.


I would say 318 sectors is already starting to be a problem, that's well above what i'd consider normal wear and tear. If it's still under warranty it'd be worth replacing it before it runs out.

---

### Post by bodhi.zazen on 2011-01-13
> **Paqman said:**
> I would say 318 sectors is already starting to be a problem, that's well above what i'd consider normal wear and tear. If it's still under warranty it'd be worth replacing it before it runs out.

+1 on checking warranty.

problem or not is often budget dependent, and different people have different tolerances, and it makes a difference production server vs old box at home.

The important thing is to bak up your data =)

---

### Post by srs5694 on 2011-01-13
> **bodhi.zazen said:**
> Keep using the HD until it is a problem.

I disagree, both in general and in this specific case. I disagree in general because disk failures can begin with just a few bad sectors and that number can increase rapidly and suddenly. If that happens, you may end up with irrecoverable problems. Thus, unless the computer doesn't hold any important data, I recommend replacing a failing hard disk at the first sign of trouble. That's why SMART (the diagnostics that are reporting problems) was invented: To spot trouble before the risks become too great, and SMART is saying there are problems.

In this specific case, Athomo has reported increasing difficulties getting the computer to boot and operate normally. Thus, the failure is already causing serious problems and must be corrected if the computer is to remain usable. (As others have said, correcting this problem means replacing the hard disk.)

One more point....

[quote=Athomo]I'm pretty sure it is because I partitioned my hard drive and ran Windows 7 Ultimate, and Ubuntu 10.04.[/quote]

This wasn't the cause of the problem. The cause was some sort of hardware failure -- probably either a drive that was defective from the factory or an old-age failure; but it could be because of a physical trauma (if it was dropped or subjected to a power surge, say) or just an early failure. Partitioning the disk and installing multiple OSes on it will *not* cause it to fail. All that partitioning the disk and using multiple OSes on it does is to lay out data in a different pattern than is common on typical single-OS installations. This changes the usage pattern, but not in a way that's dangerous.

---

### Post by bodhi.zazen on 2011-01-13
> **srs5694 said:**
> I disagree in general because disk failures can begin with just a few bad sectors and that number can increase rapidly and suddenly.

The course can be variable and this is what backups are for.

I have bad sectors on one of my laptops (it is out of warranty). I could not boot the beast as it turns out because of bad sectors in the MBR (believe it or not, although it sounds simple, that was not so easy to diagnose). Re-wrote grub and have been running the laptop for the last 18 months or so without any major problems.

When the HD fails I will decide if I want to replace it or put the $$ to a new (or used) machine.

All the important data is backed up off the HD and I know I need to save anything I really want to a flash drive.

I have seen hard drives fail much faster as well.

I think you are missing the importance of a working backup, you did not mention backups once in your post.

Hardware can fail at any time for any reason, from bad sectors on the hard drive to natural disasters to power failure to encounters with animals or children.

As long as you have backups and as long as you understand the drive is failing and could go at any time, there is no reason not to use the device.

Usually, but not always, what happens is that you start to get warnings when you boot or you get files system errors when fsck runs (I would run fsck more then every 30 boots) and at some point the hassle factor of recovering from bad sectors becomes too great. Sometimes not, sometimes there is catastrophic failure with no additional warning or sometimes the HD grinds itself to death.

I have not seen the failure of a drive affect other components, so at the time of failure drop in a new drive, reinstall your OS, and restore your data.

---

### Post by matt_symes on 2011-01-15
Hi

I have to agree with pacman and srs5694. If it was my PC, i would replace my hard drive right away with that number of bad sectors.

Sorry Bodhi. But then again, i am cautious by nature when it comes to my data. As has been stated many times in this thread, the only main safeguard is to backup, backup, backup...

As an absolute minimum, i would not use that drive as my main...

Kind regards

---

