---
title: "Do I need to use a CHKDSK-like utility?"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Kivva on 2010-07-09
Hello There!

I'm a brand new user of Ubuntu Netbook Remix (10.04). This is my first  time using a Linux based OS.

I have friends who are very happy with Linux, Ubuntu in particular. When  my boyfriend's desktop had a major failure, a friend of ours found it  to be strictly a failure of Windows Vista. So he installed Ubuntu.

I don't have a desktop, so I frequently used his... and quickly fell in  love with Ubuntu.

So today I installed UNR on my Acer Aspire One AOA150-1635.

I did a lot of research before the install, and I was delighted when I  found out that a couple of the bugs I had been on the lookout for were  already corrected.

I do have one item of concern.

Under the Disk Utility > SMART Data

[B]Under Reallocated Sector Count the assessment reads:
[COLOR=Red]Warning:
Normalized: 100
Worst: 100
Threshold: 50
Value: 164[/COLOR][/B]

At the top it also states that there are 164 bad sectors. I read that there is a utility that acts in a similar way to Microsoft's CHKDSK (although I cannot recall at this time what it was called) but users advised against using it because of the potential to damage your system and the general lack of a need to use it.

Is this an instance where using that utility would be expected? Or am I fretting over nothing?

Thanks in advance for your help!

---

### Post by dFlyer on 2010-07-10
Your hard drive is failing and you might want to backup and replace it soon.

---

### Post by Kivva on 2010-07-10
> **dFlyer said:**
> Your hard drive is failing and you might want to backup and replace it soon.

Are you sure? I was wondering it it might have been related to the fact that installing UNR I had the recovery partition deleted.

I've never had an issue in the past, and my Acer is only a year old. Beyond warranty, of course, but still... I have friends who have some much older Acers that swear by them, so the idea that the HDD is failing is a bit of a shock!

---

### Post by lindsay7 on 2010-07-10
Use the install cd to run Gparted, Look under the Partition button and run "check" on each partition.

---

### Post by 3rdalbum on 2010-07-10
To answer your subject's question, you don't need such a utility. Ubuntu checks your disks every 30 times they are mounted.

To answer your actual post: Your hard disk has 100 'spare' sectors over and above the rated capacity of your disk. If your disk detects that a sector has gone bad, it writes the data from that sector to one of the spares. You have 164 bad sectors, so there are no longer any spares remaining, and some of the data on your disk is unreadable.

Software cannot fix this problem, it is a physical failing of the disk.

Back up all important data and get a new hard disk.

---

### Post by ST3ALTHPSYCH0 on 2010-07-10
You can also, if you know the manufacturer of the HDD (this is sometimes in the BIOS) download the manufacturer's diagnostic tool. I believe most offer a bootable .iso image. It will run either a quick or a full media scan and akso read the proprietary SMART data.

---

### Post by anewguy on 2010-07-10
+1 to what 3rdalbum is saying to you - your drive is failing.  You can go with the idea of "I've had no problems" and wait for it to fail (and subsequent data loss), or you can do yourself a favor by getting a new drive, backing up your data, installing the new drive and restoring your data.  It could save you a lot of headaches at a most un-opportune time.

---

### Post by Paqman on 2010-07-10
> **Kivva said:**
> the idea that the HDD is failing is a bit of a shock!

Hard drives aren't very reliable, they do fail. Normally your drive tidies up any wear and tear on the storage medium without ever notifying you. When it detects a bad spot on the disk, it marks that spot as bad, and gets out a spare one to replace it. That's fine as long as the bad spots aren't showing up in such numbers that your disk runs out of spares. 

In your case the degradation has got to the point that the drive isn't able to guarantee that your data will be safe. From now on your stand a real risk of lost or corrupted data.

---

### Post by walt.smith1960 on 2010-07-10
Hi Kivva

Do you have access to an external DVD drive?  If it were me, I'd download clonezilla and create an image of my system.  With a drive image, I could then recreate my system exactly on a new hard drive.  I would also copy my user .home directory to some form of external backup and do so every few day. That way, if your drive does fail, you'll lose only the data since the last backup.  Hard drives do fail.  Most live a fairly long happy life, a few die young.  Here is a link to clonezilla:   

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by philinux on 2010-07-10
kivva, back up anything important now.


Just to double check those figures you've got install gsmartcontrol and compare. If it's the same and I'm betting it is your Disk is failing.

---

### Post by Kivva on 2010-07-13
Hey everyone!
 
Thank you so much for all of the advice and information, I appreciate it.
 
I don't have any data on the laptop to back up, so my real loss here is my actual HDD. One of the reasons I had sought to switch to Linux was OS stability, but I decided to go ahead and do the install when my Windows files began to turn corrupt.
 
Apparently that was more of a symptom of my harddrive begining to fail than a fault of the OS.
 
I've never had a harddrive fail, and I've done a fair share of computer restoration so I'm pretty disappointed that I have to replace my HDD. 
 
The good thing is that I have confidence I can find a replacement fairly easily given the pupolarity of the Acer Aspire One. Also, this experience has really reinforced my faith in Linux... I love the disk features that brought this to my attention versus having my HDD suddenly start smoking, lol!
 
Thanks again!  :p

---

