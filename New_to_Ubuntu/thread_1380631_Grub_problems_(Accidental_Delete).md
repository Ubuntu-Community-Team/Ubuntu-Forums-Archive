---
title: "Grub problems (Accidental Delete)"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by Trougedoor122 on 2010-01-13
[COLOR=black][FONT=Verdana]Hello Ubuntu Forums, my name is Trougedoor122 (No affiliation with Home Star Runners trogdor). I recently downloaded and installed Ubuntu 9.10 in a dual boot with Windows Vista. It worked perfectly without any problems, until I decided I was going to go back and resize some partitions; I was using the partition manager in Vista and was un-allocating some (what I thought to be) empty, unused partitions. After this I shut down the computer and came back later, what I got was this:[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]GRUB loading.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]error: no such partition[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]grub rescue>[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Obviously one of the partitions that I deleted was the grub partition and now I can no longer boot my computer, I tried several tutorials on this site but none of them helped with my problem. I understand that reformatting my hard disk is an option but would really like to avoid that route, as it will be a long process. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]If it helps I can still boot of the liveCD.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Obviously I am a novice when it comes to Ubuntu, since before I only did web programming, and any help with this matter would be gratefully appreciated. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Trougedoor[/FONT][/COLOR]

---

### Post by zvacet on 2010-01-14
Try [this.]("https://help.ubuntu.com/community/Grub2#Reinstalling from LiveCD")

---

### Post by Trougedoor122 on 2010-01-14
For some reason i can't mount my Ubuntu partition so that solution didn't work.

---

### Post by tom.swartz07 on 2010-01-14
> **Trougedoor122 said:**
> For some reason i can't mount my Ubuntu partition so that solution didn't work.

What error did it give when you tried to mount your ubuntu partition?

Try following the guide in my sig. It a little more concise.

---

### Post by mk1w86 on 2010-01-14
It looks like you might have deleted your Ubuntu partition. :(

Could you please boot the LiveCD and post the output of:

```
sudo fdisk -l
```

Also you are probably better off using GParted in future for partition editing. :D

---

### Post by Sef on 2010-01-14
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk_Download").  It can recover deleted partitions.  

>  		It looks like you might have deleted your Ubuntu partition. :sad:

I agree.  Microsoft oses cannot read non NTFS partitions, so to Win 7, Vista, XP, etc.  ext4, ext3, etc is just empty space.

---

### Post by Trougedoor122 on 2010-01-14
> **mk1w86 said:**
> It looks like you might have deleted your Ubuntu partition. :(
 
Could you please boot the LiveCD and post the output of:
 
```
sudo fdisk -l
```
 
Also you are probably better off using GParted in future for partition editing. :D
 
The results of sudo fdisk -l are included in a screen shot 
[IMG]http://4737067625499466541-a-1802744773732722657-s-sites.googlegroups.com/site/trougedoorclan/Home/Screenshot.png[/IMG]

---

### Post by tom.swartz07 on 2010-01-14
> **Trougedoor122 said:**
> The results of sudo fdisk -l are included in a screen shot 
[IMG]http://4737067625499466541-a-1802744773732722657-s-sites.googlegroups.com/site/trougedoorclan/Home/Screenshot.png?attachauth=ANoY7crKulU_KSqU0MzMzXVJrjeMz2cMtnUSRZtsFSU7jkYLhrdYvVria_szuDIGOmORq8An9DRT5YXIx0lfAZbx1AVI5IC3fzAS5wmsYa6HZEl30RzhjP5rmUkt-lqxstCiZ_PLDKOQRYepvXSbzlFepxERG_q9nCIqgcT6ayhctZcMGCFd4tWwQogNSSp2-OveNCmceFer7FqLm0tZ-OwKf-NKZWKnYA%3D%3D&attredirects=0[/IMG]

oops, try again.

---

### Post by Trougedoor122 on 2010-01-14
> **tom.swartz07 said:**
> oops, try again.
 
Fixed, sorry about that.

---

### Post by mk1w86 on 2010-01-15
> **Trougedoor122 said:**
> Fixed, sorry about that.

I still cannot see the screenshot. :confused:  

It might be easier just to copy and paste the output and post it. ;)

---

### Post by Trougedoor122 on 2010-01-15
Okay, I was able to fix the grub problems by re-installing Ubuntu, now I have access to grub, but can no longer boot Windows. The files for windows are there I just can't boot them. Also I tried using my windows CD to fix any corrupted files but the CD I got from Dell is for reinstallation only.

---

### Post by Kafubie on 2010-01-15
Oh, I remember i deleted the ubuntu partion, I got scared so I install it back on my computer.

---

### Post by langrpt on 2010-01-18
Hey I'm sorry for posting on the wrong section. 

I've recently had some problems with a hdd running Vista.
Bought a new one, installed Ubuntu - never tried it before. 

The disk was rather large, I decided to create partitions using Gparted. 
I've created new partitions, can't remember which were 'allocated'. 
One was tagged ext2, another ext3, by myself. Restarted the system and now I have a message:

GRUB loading.
error: unknown filesystem
grub rescue>_

Nothing seems to work after this. 
I'm using the latest ubuntu 9.10 (grub2?). I've tried the installation cd but it goes directly to the GRUB loading screen.
Any hints?

Thanks in advance

EDIT: anyone experiencing the same problems or similar can check this [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 15. served for me
Problem solved, apparently. Removed the hdd, installed ubuntu from the boot cd, and now it's running. I still didn't understand how to create partitions.

---

### Post by Trougedoor122 on 2010-01-20
Okay, I was able to solve the problem with a Format of my HDD and reinstalling Vista/Ubunut
 
@langrpt Yous should start a new topic

---

### Post by langrpt on 2010-02-01
I can't start a new topic.

I have a new problem, ever since I installed Ubuntu Karmic Koala I find my screen flickering for no apparent reason. 
Here's how my screen reacts (someone else's case)
[http://www.youtube.com/watch?v=D0yxFG-IMYQ](http://www.youtube.com/watch?v=D0yxFG-IMYQ)

---

### Post by mk1w86 on 2010-02-01
> I can't start a new topic.

To start a new thread go to a particular forum section e.g. Desktop Environments and select Post a New Thread under Forum Tools. ;)

> I have a new problem, ever since I installed Ubuntu Karmic Koala I find my screen flickering for no apparent reason. 

Have you tried disabling compiz? :-s

To do this go to System >> Preferences >> Appearance and then select None under the Visual Effects tab.

If this does not fix your problem start a new thread, do not keep posting in this one.

---

### Post by langrpt on 2010-02-01
Thank you very much. I'll give it a time after I disable the effects.

I'm really sorry. I don't seem to have permission to post new threads, since I can't find how to in the Thread Tools menu. Many thanks.

---

### Post by mk1w86 on 2010-02-01
> **langrpt said:**
> Thank you very much. I'll give it a time after I disable the effects.

I'm really sorry. I don't seem to have permission to post new threads, since I can't find how to in the Thread Tools menu. Many thanks.

You cannot post a new thread while viewing an existing one; go to a particular forum section (where you can see all the threads in that section) like I said in my previous post and make sure you select Forum Tools NOT Thread Tools which only appear when viewing a thread.

---

### Post by langrpt on 2010-02-01
**langrpt**, you do not have permission to access this page. This could be due to one of several reasons:
  
[LIST=1]
[*]Your user account may not have sufficient privileges to access this page. Are you trying to edit someone else's post, access administrative features or some other privileged system?
[*]If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.
[/LIST]

---

