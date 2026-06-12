---
title: "I'm half way to lose my mind - Ubuntu 10.04"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by amjjawad on 2010-09-09
Hi everyone,

Well, this is a bit weird and I'm not sure what's going on so hopefully someone does and could help me out!

Let me first tell you what kind of PC/configuration I do have:
I have a desktop PC (P4) with 2GB of RAM, two SATA HDDs, one IDE HDD (40GB), Windows 7 on HD1 (SATA). I had some hard time to download Ubuntu (download failed in the process) so finally I decided to use torrent to get it. I burned the iso image to a blank CD and started Wubi to install Ubuntu 10.04 on my**_ 40GB IDE HDD_**. 

Wubi started to install files, for some reason my CD got ejected (not sure why) and Wubi asked me either to restart now or do it manually later. I chose to restart now without the CD (I thought it doesn't require a CD as it got ejected). When nothing happened, I put the CD back and restart my PC. So far, so good.

When the installation steps appeared, I chose my location, language, etc and then I chose:
**Erase and use the entire disc** in step 4 and of course I chose my [B][U]40GB IDE HDD.
[/U][/B]The last step I did in the installation wizard was choosing the loader to be from my [B][U]40GB IDE HDD and I'm afraid that caused the problem.

[/U][/B]Now, what happened is: suddenly, I got an error message, not sure what exactly it said but in general, it said that my HD is either too old or damaged and need to be replaced, then the installation process stopped working or ended.
I restarted, there was an option to choose between Windows or Ubuntu but nothing happened with I chose Ubuntu.
When I booted from Windows 7, I couldn't find my [B][U]40GB IDE HDD and it's gone/missing :(
[/U][/B]I tried to reboot from the CD (ubuntu 10.04) many times but all what I got is the Ubuntu logo in the middle with 5 dots and it seems something is loading but nothing happens. I was waiting for 15mins or more but still, nothing.

All what I can do is boot from Windows 7. Everything is fine with Windows, I have no problem but I can't get my **_40GB IDE HDD _**back, can't boot from ubuntu nor can install it again.

I'm not sure whether it was my mistake from the beginning to choose Wubi or it was my mistake when I changed the loader option? not sure what's going on.

I tried to search the forum for similar issue but I couldn't find one.

Is there someone who could possibly help me, please?
I need my [B][U]40GB IDE HDD back and I want to install Ubuntu.
[/U][/B]If something wrong with my configuration or anything, please let me know.

Thanks a lot!

---

### Post by grief -l on 2010-09-09
Not a big problem, it's just that windows can't read the (linux) filesystem on the ide disk. It sounds like your CD is corrupt (you can check it with Md5Checksum - google is your friend). Burn a new one at lowest speed possible and on a CD-R disk, and boot directly from the CD (don't use wubi) to test the CD and your hardware and then to install.

---

### Post by amjjawad on 2010-09-09
> **grief -l said:**
> Not a big problem, it's just that windows can't read the (linux) filesystem on the ide disk. It sounds like your CD is corrupt (you can check it with Md5Checksum - google is your friend). Burn a new one at lowest speed possible and on a CD-R disk, and boot directly from the CD (don't use wubi) to test the CD and your hardware and then to install.

Hi,

I'm aware of that Windows can't read the Linux drive/file system, thank you :) but problem is I can't even access that drive (40GB IDE HDD) from Ubuntu itself. Even when I reboot using the CD, unless as you assumed, the CD is corrupted.

I used Windows 7 built-in Burner and didn't use any other Software. I'll try to burn another copy but not sure if that would fix it.

By the way, there's nothing wrong with my 40GB IDE HDD and it was working perfectly few days ago when I had Vista before installing Windows 7.

Thank you!

---

### Post by Hobgoblin on 2010-09-09
I suspect your 40GB IDE drive has died.

Can you see it in disk management in Windows?

Can the BIOS see it?

Try downloading the (HDD) manufacturer's diagnostic tools and test the drive.

---

### Post by amjjawad on 2010-09-09
> **Hobgoblin said:**
> I suspect your 40GB IDE drive has died.

Can you see it in disk management in Windows?

Can the BIOS see it?

Try downloading the (HDD) manufacturer's diagnostic tools and test the drive.

Negative. Both Windows Disk Management and BIOS can detect/see the 40GB IDE HDD but I can't access it neither in Windows nor Ubuntu.
Yes, I know Windows doesn't read Linux/Ubuntu file system/drive but Ubuntu doesn't read/access that too.

I have no idea how to fix that or at least can access my HD so that I can install Ubuntu again?

Thanks :)

---

### Post by grief -l on 2010-09-09
You could try using GParted in the Administration menu, or cfdisk from a terminal and use either to just rewrite the partition table.

---

### Post by amjjawad on 2010-09-09
> **grief -l said:**
> You could try using GParted in the Administration menu, or cfdisk from a terminal and use either to just rewrite the partition table.

My friend, how would I use that while I can't access Ubuntu to being with?
Check again what I wrote above :)
I can't access Ubuntu or in a better words, I don't have Ubuntu yet. It's just a name in the booting Menu, that's all.

I burned another copy using Infra Recorder but same thing happened, I just get that logo with the 5 dots, that's all (as I explained in my 1st post).

---

### Post by vert11 on 2010-09-09
Hi all,
I am an absolute beginner in this field but,,,

seems that the file system on your 40 GB drive is not installed properly.Try formatting that drive with ntfs(using any windows bootavle disk),then from the partition manager delete the partition,making it as unallocated space,and then allow ubuntu to find that partition automatically....

---

### Post by amjjawad on 2010-09-09
> **vert11 said:**
> Hi all,
I am an absolute beginner in this field but,,,

seems that the file system on your 40 GB drive is not installed properly.Try formatting that drive with ntfs(using any windows bootavle disk),then from the partition manager delete the partition,making it as unallocated space,and then allow ubuntu to find that partition automatically....

The only option I got or can do is "delete" the partition using Windows Disc Management (I got two partitions by the way which have been set by Ububtu during installation) but I'm not quite sure whether it's advisable to "delete" these two partitions or not?

---

### Post by amjjawad on 2010-09-09
Well, as long as I started the installation on another HDD and didn't touch Windows-Partition, I figured out that Windows MBR is untouchable in this case (correct me if I'm wrong, please), hence I deleted the two partitions set by Ubuntu (which didn't work anyway) and formatted the whole HDD using NTFS file system. Now, I can access my 40GB IDE HDD but can't (of course) get rid of "Ubuntu" option in the boot menu.

Not very sure how to do that?
I'll try to search in other posts but if someone knows, please let me know.

Thanks!

P.S.
I'll try to install Ubuntu later (not using Wubi) on the same HD (40GB). Hopefully I won't get the same issue.

---

### Post by dcsoldschool53 on 2010-09-09
ok, first off, you can only use the ubuntu CD one time. Once you burn the .ISO to a cd, and use it. You will have to burn the .ISO file to another CD. With CD's they are a one time use only. You can burn that .ISO file as many times as you want.
Second, how are you dual booting windows and ubuntu? I see that you are using ubuntu 10.04, but I have 9.04 and I had to configure the menu.list in grub to get them both to work properly. Ubuntu 10.04 use grub2.

---

### Post by MacinViLLe on 2010-09-09
> **dcsoldschool53 said:**
> ok, first off, you can only use the ubuntu CD one time. Once you burn the .ISO to a cd, and use it. You will have to burn the .ISO file to another CD. With CD's they are a one time use. You can burn that .ISO file as many times as you want.

I have installed Ubuntu 10.04 with over 20 PCs in our office using only one burned Ubuntu ISO. As a matter of fact, I am reformatting this PC beside me using the same ISO I burned last month.

> **dcsoldschool53 said:**
> Second, how are you dual booting windows and ubuntu? I see that you are using ubuntu 10.04, but I have 9.04 and I had to configure the menu.list in grub to get them both to work properly. Ubuntu 10.04 use grub2.

Yeah, I think it is the GRUB2 that makes you choose your operating system. I have the same problem with my Vista computer, which used to be dual booted with Ubuntu 10.04. It's like GRUB2 is tattooed in the MBR of somewhere inside, because I have already deleted and reformatted the hard drive and still GRUB2 appears. I'm not sure with this though:p

---

### Post by dcsoldschool53 on 2010-09-09
Sorry MacinVille. What I meant to say was that the CD that he burn the iso file to, can be used after a certain amount of time. But after that the CD start to work funny...it loose it ability to work right.

---

### Post by Clever_Username on 2010-09-10
> **dcsoldschool53 said:**
> Sorry MacinVille. What I meant to say was that the CD that he burn the iso file to, can be used after a certain amount of time. But after that the CD start to work funny...it loose it ability to work right.

Never heard that one before

---

### Post by MacinViLLe on 2010-09-10
> **dcsoldschool53 said:**
> Sorry MacinVille. What I meant to say was that the CD that he burn the iso file to, can be used after a certain amount of time. But after that the CD start to work funny...it loose it ability to work right.


No problem dcsoldschool53. I agree that after some time a CD won't work anymore, maybe due to scratches or being exposed to direct sunlight or strong magnetic fields. Or maybe (just maybe) the CD-ROM used to run the CD is scratching it (not sure if it's even possible, just a guess ;)). 

Going back to the problem, the only way I know on how to uninstall GRUB2 is through a linux terminal, and type ```
sudo aptitude purge grub2 grub-pc
``` Not so sure on how to do it with Ubuntu deleted.

---

### Post by jtarin on 2010-09-10
Installing WUBI to my mind was a mistake also...but that is my personal opinion. Are you still using the Windows loader and now it has an extra entry? To edit this and return your boot to normal look at my signature for a link to EasyBCD. It will allow you to edit your Windows loader.
I'm not responsible for your not reading directions on usage. There is a forum there if you are not able to read and follow directions.

---

### Post by samstreet101 on 2010-09-10
I say use gparted to reformat/partition the 40GB IDE drive. You don't have to access it from Ubuntu, you can download and burn a separate ISO of gparted so you can run it from a disc.

---

### Post by mastablasta on 2010-09-10
Mistake no. 1: you are using Wubi. Wubi creates sort of a virtual instalation of the system within Windows. basically one huge file as i understand.
 
 
What you want is a dual boot. already prepared the 40 GB partition/disk so you should just put the ubuntu there (through normal install). It will work much faster and you will have less problems with it.
 
now what you need to do is get gparted (i think it's on Ubuntu disk and can be used if you boot from CD) or maybe even windows partition manager to see that partition, delete it/format it and then when you are done you need to stick the CD inside boot the system from CD (select boot form CD in BIOS boot menu) and install from there. Yyou can also try the system here in live session that won't make any changes on your hard disk - it runs from CD but is much slower than the real deal. However it does help you to test if everything will work smooth later on. when it comes to the question where to install select the free hard disk. Ubuntu will do partitioning of it for you. then reboot after install and all should be ok (hopefully). if not post back or search for the issue. because you might need to do some grub update (if ubuntu is on another disk) or not.

---

### Post by amjjawad on 2010-09-10
> **MacinViLLe said:**
> No problem dcsoldschool53. I agree that after some time a CD won't work anymore, maybe due to scratches or being exposed to direct sunlight or strong magnetic fields. Or maybe (just maybe) the CD-ROM used to run the CD is scratching it (not sure if it's even possible, just a guess ;)). 

Going back to the problem, the only way I know on how to uninstall GRUB2 is through a linux terminal, and type ```
sudo aptitude purge grub2 grub-pc
``` Not so sure on how to do it with Ubuntu deleted.

Sorry guys but what are you talking about is way far and different from what I'm talking about here. My CD is NEW and I just burned the CD few mins before I use it so how come it's damaged? not to mention I've done that (burned) two CDs and both got the same issue with installation so I don't think it has anything to do with the CD itself :)

---

### Post by amjjawad on 2010-09-10
I'm sorry guys but apparently, no one understands what I mean nor my real problem.
[COLOR=Red]**First thing first, I can't login to ubuntu because simply I couldn't install it to begin with.**[/COLOR] Installation of ubuntu starts for few mins then an error message popped up.

Now, to make it clear, forget what I've said before and here's my problem:

I'm using new CD to install Ubuntu. I used Microsoft Disc Management to delete ubuntu's partitions and I got my 40G IDE HDD back. The problem is worse if you ask me. I have a problem with my SATA HDD and I lose it (BIOS can't read it) every time I shut down my PC but I can ONLY restart it so that I can access Windows 7. That's why I need sort of backup OS in case my SATA HDD will die. Also, I'd love to try the new Ubuntu because I had 9.10 before and I had no problems with installation or usage whatsoever. I'm having problems with the new version now.

I got this error msg and it popped up after installation began with 2 or 3 mins. NO, I did not used Wubi because it seems almost everyone is against it and I understand why is that. After I got back my 40G IDE HD, I tried to install Ubuntu for the 3rd time from a new CD (it wasn't under the sun or something, trust me :P) and I chose "Erase and use the entire disc" option. Of course I booted it from the CD and I did not use Wubi (to make it extra clear).
The msg I got was and that was few mins after the installation began (yes, after I finished the 7 steps):

****************************************************************
[COLOR=Purple][B]Installation Failed
The installer encountered an error copying files to the hard disk:
[Errorno 30] Read-Only File System: '/target/bin'

This often due to faulty hard disk. It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.[/B][/COLOR]
*********************************************************************

Trust me, there's nothing wrong with my HD (40G IDE) because a week ago or less, I had vista installed on that one and it can be detected by BIOS (except it reads it as SCSI not sure why) and Windows. I guess there's something wrong either in the step, in the image or in the process or perhaps I should not use that drive? I really don't know?

That's all what I need to find out and fix. I have to have another OS just in case my PC will stop working, I mean my SATA HDD will die.

Now, how would I fix that and get Ubuntu? I don't want to use the old one (9.10) because I hate to give up, unless there's a real problem with 10.04 or my Hardware.

Thank you!

---

### Post by amjjawad on 2010-09-10
> **mastablasta said:**
> Mistake no. 1: you are using Wubi. Wubi creates sort of a virtual instalation of the system within Windows. basically one huge file as i understand.
 
 
What you want is a dual boot. already prepared the 40 GB partition/disk so you should just put the ubuntu there (through normal install). It will work much faster and you will have less problems with it.
 
now what you need to do is get gparted (i think it's on Ubuntu disk and can be used if you boot from CD) or maybe even windows partition manager to see that partition, delete it/format it and then when you are done you need to stick the CD inside boot the system from CD (select boot form CD in BIOS boot menu) and install from there. Yyou can also try the system here in live session that won't make any changes on your hard disk - it runs from CD but is much slower than the real deal. However it does help you to test if everything will work smooth later on. when it comes to the question where to install select the free hard disk. Ubuntu will do partitioning of it for you. then reboot after install and all should be ok (hopefully). if not post back or search for the issue. because you might need to do some grub update (if ubuntu is on another disk) or not.


Thanks a lot but I know most of what you wrote already and my problem with Ubuntu is a bit bigger than that. There's update in my problem so please check my previous post :)

---

### Post by mastablasta on 2010-09-10
Ok what they were trying to say is that while you downloaded the file to (a faulty?) disk and burned it it can develop errors. The CD is then not the same as original.

anyway... about the disk. you said windows works ok. why not do a diskcheck with windows? 
[http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors](http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors)

Also if you can get another cable and switch them. it could be just the cable that is malfunctioning. i had this issue and MS support said my disk is faulty or dying. turns out it was just the cable as the disk runs fine now...

again before instalation try to boot from CD. put the CD in and set the bios to boot from CD. don't install this time just run the system. that way you can also see if everything works OK. live session should work even if your hard disk died i believe since the system is tranfered to RAM (someone might correct me on this?!) and uses CD.

Another thing that popped into my mind is you said you have problem with your primary disk, btu you see Linux will want to write something there too i believe. and that would be at least GRUB if nothing else. could it be that the error is there because it can't write to it? someone else will have to help you with that.


but just to reassure you even if your disk "dies" you should be able to boot at least from CD into Live session and then try to recover the data (unless the disk is really badly damaged).

---

### Post by grief -l on 2010-09-10
for somebody whose looking for help you sure aint easy to please.

check the CD's Md5Checksum (use google if you have to)

check the CD on another computer if you have to

download GParted and burn it to CD and use it to solve your problem. you can even remove all other disks while bust with the problematic one

---

### Post by mastablasta on 2010-09-10
> **grief -l said:**
> 
check the CD's Md5Checksum (use google if you have to)


Yes this is also important to do before you begin with your install.

---

### Post by amjjawad on 2010-09-10
> **mastablasta said:**
> Ok what they were trying to say is that while you downloaded the file to (a faulty?) disk and burned it it can develop errors. The CD is then not the same as original.

anyway... about the disk. you said windows works ok. why not do a diskcheck with windows? 
[http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors](http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors)

Also if you can get another cable and switch them. it could be just the cable that is malfunctioning. i had this issue and MS support said my disk is faulty or dying. turns out it was just the cable as the disk runs fine now...

again before instalation try to boot from CD. put the CD in and set the bios to boot from CD. don't install this time just run the system. that way you can also see if everything works OK. live session should work even if your hard disk died i believe since the system is tranfered to RAM (someone might correct me on this?!) and uses CD.

Another thing that popped into my mind is you said you have problem with your primary disk, btu you see Linux will want to write something there too i believe. and that would be at least GRUB if nothing else. could it be that the error is there because it can't write to it? someone else will have to help you with that.


but just to reassure you even if your disk "dies" you should be able to boot at least from CD into Live session and then try to recover the data (unless the disk is really badly damaged).


I have 3 HDDs and I wouldn't download Ubuntu iso file on a faulty HDD, that's why I do have 3 :)
I might be a noob with Linux but I'm not with PCs in generals.

Windows works fine unless I turn my PC off so I won't do that, at least now.

Which disk you want me to check? I don't get it? if you're talking about the disk that I'm installing Ubuntu on, so YES, I just used FULL FORMAT and Check it and it's fine and error free.

As far as I can tell with my many years with PCs, if there's something wrong, I mean hardware issue, the device will not working. Hardware errors are not like Software errors. If the cable is faulty then BIOS should not be able to read it nor Windows but that's not true, both BIOS and Windows can read and access my 40G IDE HD which is the same drive I want to install Ubuntu on and get that error msg.

I know about the BIOS priority :) and I might take your advice to try Ubuntu without installation even though I don't think that would fix the problem, the problem is something else I can't figure it out yet. Anyway, I'll give it a try :)

No, Ubuntu has nothing to do with my 1st SATA HDD. Last time I tried to install, BIOS couldn't read my SATA HDD, hence Ubuntu couldn't detect Windows. It was like I'm installing Ubuntu on a brand new PC that has 2 HDD if you know what I mean. So, it has nothing to do with my main SATA HDD. In fact, that's why I want to use my 40GB IDE HDD to install Ubuntu but I just can't.

Long story short, let's forget about other HDDs. Let's talk about my 40GB IDE HDD because I'm using that one to install Ubuntu. I told you guys about my problem in general to give better idea about the whole situation but looks like I created more confusion :P sorry!

I'll check the CD, I checked my 40GB HDD already and it's error free and I'll try Ubuntu without installation. 

Let's see what could happen!

---

### Post by amjjawad on 2010-09-10
> **grief -l said:**
> download GParted and burn it to CD and use it to solve your problem. you can even remove all other disks while bust with the problematic one

I don't need that, as I wrote earlier, I'm able to access my 40GB IDE HDD now so that's not the issue anymore :)

Thanks anyway. I'm going to check the CD and see what could happen!

---

### Post by Gunman1982 on 2010-09-10
> **amjjawad said:**
> 
As far as I can tell with my many years with PCs, if there's something wrong, I mean hardware issue, the device will not working. Hardware errors are not like Software errors. If the cable is faulty then BIOS should not be able to read it nor Windows but that's not true, both BIOS and Windows can read and access my 40G IDE HD which is the same drive I want to install Ubuntu on and get that error msg.

Then let me tell you that hardware errors are much worse than software errors resulting in a system which is highly unstable and often shows errors which are hard to reproduce. 

A friend of mine has an external drive which works fine but he can't repartition it because a controller seems to be busted. So I wouldn't bet on your drive being fault free.
However, I would suggest that you boot up the cd as the live system. Start gparted and partition the 40GB drive manually. After you did this and it workedyou know that the problem is not the partitioning process. Next try to mount those newly created partitions and write something to them. Or you could try to run an 'fsck' on that partition (checks the filesystem for errors)

---

### Post by amjjawad on 2010-09-10
> **Gunman1982 said:**
> Then let me tell you that hardware errors are much worse than software errors resulting in a system which is highly unstable and often shows errors which are hard to reproduce. 

A friend of mine has an external drive which works fine but he can't repartition it because a controller seems to be busted. So I wouldn't bet on your drive being fault free.
However, I would suggest that you boot up the cd as the live system. Start gparted and partition the 40GB drive manually. After you did this and it workedyou know that the problem is not the partitioning process. Next try to mount those newly created partitions and write something to them. Or you could try to run an 'fsck' on that partition (checks the filesystem for errors)

Yes, and it hate Hardware errors specially when you need to buy new HD :)

Thanks, I'll do that and see what could happen. It's extra clear and I see that you got my point :)

Will keep you updated ...

---

### Post by amjjawad on 2010-09-10
> **Gunman1982 said:**
> Then let me tell you that hardware errors are much worse than software errors resulting in a system which is highly unstable and often shows errors which are hard to reproduce. 

A friend of mine has an external drive which works fine but he can't repartition it because a controller seems to be busted. So I wouldn't bet on your drive being fault free.
However, I would suggest that you boot up the cd as the live system. Start gparted and partition the 40GB drive manually. After you did this and it workedyou know that the problem is not the partitioning process. Next try to mount those newly created partitions and write something to them. Or you could try to run an 'fsck' on that partition (checks the filesystem for errors)


Ok, I did exactly what you suggested. I booted from Ubuntu 10.04 CD and chose the first option (try Ubuntu) and I'm writing this post while I'm on Ububtu. I did many operations on my 40GB IDE HDD.

I removed all the partitions, create new partitions (3) and transfered 10GB to the larger partition and about 1.6GB to the other 2 partitions. Also, I checked the whole HDD (40GB) and it said:
**[COLOR=Blue]"File System is Clean"[/COLOR]**.

The only thing that happened is the Disc Utility program stopped working many times while I was checking my 40GB IDE HDD. Of course I had to unmount the 3 partitions before the check up but I have no idea why the program (Disc Utility) stopped working in the process?

Now, what's next? it seems fine and nothing wrong with the HDD as far as I can tell. I'll add two screen shots for more info.

Screen shot 1: Before any operation
[http://i52.tinypic.com/4tx7j4.jpg](http://i52.tinypic.com/4tx7j4.jpg)

Screen shot 2: After deleting the previous partitions and create new ones
[http://i53.tinypic.com/10f0pye.jpg](http://i53.tinypic.com/10f0pye.jpg)


[COLOR=Red]So, what's next???[/COLOR]

Thank you :)

---

### Post by Gunman1982 on 2010-09-10
Ah ok, ntfs, thats windows and not really suitable to install Ubuntu on. So delete them :-P

Now you could try to create those partitions so the installationprocess of ubuntu can use them. 
You should create at least 2 partitions, one of the type ext4 and another swap partition which should have the size of 2 times your RAM (1GB Ram -> 2GB SWAP).
I would suggest to have the ext4 partition first and then the SWAP partition.

Now you could try the install process again and say that you want to manually partition the hdd. At that step you set the ext4 partition to have the mount point as / and the swap partition as swap.

Oh yeah I nearly forgot, I took a screenshot of how I partitioned my hdd [http://i54.tinypic.com/315h40n.png]("http://i54.tinypic.com/315h40n.png")
The reason I have seperated /boot and / is because of old times.

---

### Post by jtarin on 2010-09-10
amjjawad could you possibly stop the practice of making your complete posted text in colors, links and certain highlights are fine? It is a little distracting. Thanks

---

### Post by amjjawad on 2010-09-10
> **Gunman1982 said:**
> Ah ok, ntfs, thats windows and not really suitable to install Ubuntu on. So delete them :-P

Now you could try to create those partitions so the installationprocess of ubuntu can use them. 
You should create at least 2 partitions, one of the type ext4 and another swap partition which should have the size of 2 times your RAM (1GB Ram -> 2GB SWAP).
I would suggest to have the ext4 partition first and then the SWAP partition.

Now you could try the install process again and say that you want to manually partition the hdd. At that step you set the ext4 partition to have the mount point as / and the swap partition as swap.

Oh yeah I nearly forgot, I took a screenshot of how I partitioned my hdd [http://i54.tinypic.com/315h40n.png](http://i54.tinypic.com/315h40n.png)
The reason I have seperated /boot and / is because of old times.

Hahaha, yes, I know NTFS isn't for Ubuntu but I was just playing around and testing, that's all :)

Ok, I think I'm more than half way to lose my mind :confused:
I did exactly the same as you suggested except:
1- I created 4GB ext4 partition for /boot
2- I chose that partition (/boot) to install the loader

And ................................. SAME error message once more in the 15% of the progress :(

Oh boy, I'll seriously lose my mind ... I don't know what's wrong?!

P.S.
Am I doing something wrong in here?
[http://i52.tinypic.com/15gvvdg.jpg](http://i52.tinypic.com/15gvvdg.jpg)

---

### Post by jtarin on 2010-09-10
OK bear with me because its difficult to follow this thread. Do you still have Windows on your drive? If yes do you want to keep it?
If no there is only one solution left to try. If your hard disk is bad even this solution probably will not work.Delete all your partitions but the swap. Allow Ubuntu to automatically configure itself upon install. In otherwords allow it to use the entire disk and proceed with the install from there. If you get the error again I'm afraid you have drive problems and the only other option I can think of go to your drive manufacturers site and see if they have tools for you to correct it.It will be something to load onto a floppy or USB flash.

---

### Post by jtarin on 2010-09-10
[Here's a link ]("http://ubuntuforums.org/showthread.php?t=564726")on doing some checking on your hard drive using the Live CD....maybe a few things you would like to try. Might get some valuable information along the way.

---

### Post by amjjawad on 2010-09-10
> **jtarin said:**
> OK bear with me because its difficult to follow this thread. Do you still have Windows on your drive? If yes do you want to keep it?
If no there is only one solution left to try. If your hard disk is bad even this solution probably will not work.Delete all your partitions but the swap. Allow Ubuntu to automatically configure itself upon install. In otherwords allow it to use the entire disk and proceed with the install from there. If you get the error again I'm afraid you have drive problems and the only other option I can think of go to your drive manufacturers site and see if they have tools for you to correct it.It will be something to load onto a floppy or USB flash.


Yes, I do have Windows 7 and yes, I want to keep it as long as my main SATA HDD is working.
I might go for your plan/suggestion while everything as it's with the other HDDs. I'll just remove the two partitions on my 40GB IDE HDD and keep SWAP as you suggested but guess what? I just tried Ubuntu 9.10 and I got "exactly" the same error message :(

---

### Post by amjjawad on 2010-09-10
Hey buddy, guess what? I tried Ubuntu 9.10 few mins ago (because honestly I'm a bit giving up from Ubuntu 10.04) but ... I got exactly the same issue :(

I did that because I suspected something is wrong with my CDs or the ISO file that I downloaded using torrent. I couldn't use direct download because my internet connection is so bad and I have to wait 6-7 hours, not to mention the disconnection in the process.

I guess there are two options left:
A- Forget Ubuntu at the moment
B- Check my HDD (40GB IDE) somehow with some other tools.

So far, all the tools said it's error free so not sure what could be the real problem.

---

### Post by jtarin on 2010-09-10
You tried 9.10 before or after deleting all partitions?

---

### Post by amjjawad on 2010-09-10
> **jtarin said:**
> You tried 9.10 before or after deleting all partitions?

I have tried it after Ubuntu 10.04 failed to install for the 10th times. Same last partitions in this screen shot:

[http://i52.tinypic.com/15gvvdg.jpg](http://i52.tinypic.com/15gvvdg.jpg)

---

### Post by jtarin on 2010-09-10
OK...run a filesystem check. Boot the Live CD and run the command
  ```
sudo e2fsck -C0 -p -f -v /dev/sdc1
```

Can you give the name and model number of the drive?

---

### Post by amjjawad on 2010-09-10
> **jtarin said:**
> OK...run a filesystem check. Boot the Live CD and run the command
  ```
sudo e2fsck -C0 -p -f -v /dev/sdc1
```Can you give the name and model number of the drive?

I know this is so silly but I have no clue how shall I do that? I've never used any command with Ubuntu and not sure how?

For now, I'm on Windows 7. I'm downloading a tool for my Maxtor 40GB IDE HDD, hopefully I could tell whether it's faulty or what?

---

### Post by jtarin on 2010-09-10
> **amjjawad said:**
> I know this is so silly but I have no clue how shall I do that? I've never used any command with Ubuntu and not sure how?

Boot the Live CD and select TRY. When your at the desktop select Applications>Accessories>Terminal. When the terminal appears enter the command as I have show. It will tak sometime to run....let it finish and record the output and post.

---

### Post by jtarin on 2010-09-10
This is the first time I ave seen your type of HD listed. I assume this is a hard drive from another machine? Have you set this one up to be a slave drive in the bios,HD jumper and on the cable? Look to Maxtor for correct settings to use this drive as a secondary (slave) drive.

---

### Post by Hobgoblin on 2010-09-10
> **amjjawad said:**
> 
Ok, I think I'm more than half way to lose my mind :confused:
I did exactly the same as you suggested except:
1- I created 4GB ext4 partition for /boot
2- I chose that partition (/boot) to install the loader

And ................................. SAME error message once more in the 15% of the progress :(


In my experience the most likely cause of that is faulty RAM.  Select the memtest option from the Ubuntu CD and let it run for a few hours.

---

### Post by vert11 on 2010-09-10
yeah as u said nothing is working then there mus be something wrong with ur hardware.....
and ya you told that the option is to "forget Ubuntu",why so???
Try using virtual box(oracle) or virtual pc(microsoft) in ur windows7 partition then install linux in them.....

---

### Post by anewguy on 2010-09-10
I'm going to throw a couple of things at you ;) :

- hardware errors.  Trust someone with a lot of experience in this regard:  you can have hardware errors that aren't hard fail errors.  Instead they'll drive you nuts with all kinds of screwy things happening that don't seem to make sense.  Bad cable?  Could be - again, unless a hard fail, it will depend on the "driver" (I use that term loosely here) and how much it can detect and/or correct for errors - 1 bit errors can usually be corrected in the transfer.

- your last picture of the screen from gparted shows something I've never seen before:

/target in the front of the mount point

I know you need at least /, and with 2 partitions I think the next one is usually just recommended to be /home.  This keeps user files separate from the system files if you do a re-install or an update to a new release.  Perhaps the /target is just something I haven't seen, but it just doesn't look right.

- about the CD:  as mentioned, be sure you have checked the md5 sum against the ISO image you downloaded.  I believe you could have a faulty download - as an example some file corrupted, but still have a valid file system which is what the check you ran would only tell you.

- my recommendation:  Using a LiveCD and running gparted, remove all partitions from your 40gig drive - do not create any after you have removed all of them.  Completely unplug the cables going to all of your other hard drives.  For your 40gig drive (I believe you said it's IDE?) be sure to set the BIOS so only that drive is recognized and is set as the boot device. With the LiveCD running, select install Ubuntu.  If you only have 1 disk recognized, which should be the case with the other cables removed, just let it install using all of your drive - don't do the option to define your partitions.  Let that go and see if it installs - it should - if not, stop, and post back the error messages.  If it does complete, do a restart and remove the LiveCD so it boots from the 40gig drive.  Grub will have been installed to that drive only, and will only be aware of Ubuntu.  Once this is all able to boot, the other drives can be added back in.  If you want the option to boot Windows or Linux - e.g. the grub menu, only update grub on the 40gig drive and always leave it as the boot device in the BIOS.  You'll be able to run Windows from there once grub is updated, something we can easily walk you through.

I suggest this since you are having so many problems.  Checking the md5sum, and perhaps (as others have found) burn a new CD at the slowest speed your drive will do, should give you a good CD.  Next, by physically removing all cables to your other drives, we are eliminating anything external to the 40gig drive from causing problems (except, of course, for things like a controller that is faulty, a cable that is faulty, memory that is faulty, etc.).  Once you can actually get Ubuntu installed only to the 40gig drive, with no other drives known, we can work with you to add your other disks back and give you dual-boot Windows or Ubuntu without changing the mbr on your Windows disk.

Dave ;)

---

### Post by BobJam on 2010-09-11
> **amjjawad said:**
> I couldn't use direct download because my internet connection is so bad and I have to wait 6-7 hours, not to mention the disconnection in the process.That sounds like you use dial-up.  It also sounds like all these ISO's you're downloading via dial-up (or a very very bad broadband connection) are corrupted from the get-go.  Consequently, you're doomed right out of the gate.

That fits with your explanation that Windows can "see" your 40GB HDD, and your claim that the HDD is error free.

I wouldn't necessarily rule out a faulty HDD, but from what you say that's unlikely.

The only thing left that I can think of is a corrupted download.  Have you checked the md5 sums?

In any case, you can rule out corrupted downloads simply by ordering the CD from Canonical.  I realize that will take some time, but since you've already spent what I assume is a considerable amount of time downloading and troubleshooting, what's another few days?

If you still get the installation error message with the CD from Canonical, then at least you can deduce that it's not a corrupted download issue.

BTW, another troubleshooting suggestion . . . try installing Ubuntu on another HDD.  You can halt the process before it does the formatting, but at least you'll be able to see if it gets past that initial error message.  If so, that would point to the 40GB HDD as the culprit.

I see your problem as being in one of three areas:

1.  Faulty ISO download.

2.  Faulty 40GB HDD

3.  Faulty installation method.

1 and 2 would be relatively easy to determine.  3 may be an issue for you to pursue if you rule out the other 2.

---

### Post by amjjawad on 2010-09-11
> **Hobgoblin said:**
> In my experience the most likely cause of that is faulty RAM.  Select the memtest option from the Ubuntu CD and let it run for a few hours.

Negative. If it's a faulty RAM, then the whole PC will not even turn on ;)

---

### Post by amjjawad on 2010-09-11
> **jtarin said:**
> This is the first time I ave seen your type of HD  listed. I assume this is a hard drive from another machine? Have you set  this one up to be a slave drive in the bios,HD jumper and on the cable?  Look to Maxtor for correct settings to use this drive as a secondary  (slave) drive.

Well, I've never used the Terminal before so thanks a lot for showing how to do that :)

I formatted the HDD again so I couldn't run the test. It says it must be  ext2 and it's NTFS at the moment. I'll do that test later because I'm  thinking about something else that could fix the problem.

I know everything about the jumper, BIOS settings, etc. My Maxtor 40GB  IDE is connected to IDE 1 (I have 3 - IDE 0, IDE 1 and IDE 2) and it's  alone so it's Master. It has nothing to do with my other two SATA HDDs.

My plan is as follows:
I'm going to swap between my DVD Driver (connected to IDE slot 0) and my  Maxtor 40GB HDD (connected to IDE 1 slot). Also, I'm going to swap  their cables.
I'll do that for two reasons:

A- Give it one more try (could be the last one)
B- I'm concerned about one fact that I know since the very beginning of  all this which is my BIOS read my Maxtor 40 GB IDE HDD as SCSI which is  not, it's IDE so I'm just concerned that Ubuntu for some reason can't  install itself on such drive with such settings that have been  determined by BIOS.

I'll do that and will keep you informed ;)

Thanks a lot!

---

### Post by amjjawad on 2010-09-11
> **vert11 said:**
> yeah as u said nothing is working then there mus be something wrong with ur hardware.....
and ya you told that the option is to "forget Ubuntu",why so???
Try using virtual box(oracle) or virtual pc(microsoft) in ur windows7 partition then install linux in them.....

If I ever have to give up, then that would be for one good reason. My doctor ordered me to stay away from my PC because I have some problems with my eyes. I'm spending so much time on this and I woke up this morning with a very strong headache. Ubuntu won't give me another eyes, right? :)

---

### Post by amjjawad on 2010-09-11
OMG, I'll yell, I'll shout, I'll .... AAAAAAAAAAAA

After swapping between IDE 0 (DVD Driver) and IDE 1 (Maxtor 40GB HDD) and the cables too, my BIOS couldn't detect the DVD driver, so I'm without a DVD driver now (but I can see/read to/from my Maxtor HDD (which is not helpful because I can't install without a CD). 

Actually, I got that problem few days ago but being busy with Ubuntu made me forget that.

So, either the cable (which was connected to my Maxtor HDD) is faulty but I doubt that because I was able to access and do anything on my Maxtor HDD or my Botherboard/BIOS has an issue with the other free IDE slots. I double checked my BIOS settings many many times to find an option to unable disable anything but couldn't find any that has something to do with my issue. My MB is Gigabyte BTW.

Hmmmmm, I don't know what else I didn't try?!

---

### Post by ubunwhat on 2010-09-11
Hey brother, a few observations from a fellow noob who found himself well more than half way to cranial meltdown during installation less than a week ago.

For starters, as someone else suggested it really sounds as if your iso is bad.  I had this problem the first time that I tried to install Ubuntu and had to download from another source, wipe everything clean, and start over.  

Second, and this is really the part that had me talking to myself, the issue that you were getting when you did manage to get at least some piece of an installation going ( the Ubuntu screen with the five dots that look like they are doing something but actually don't ) gave me flashbacks.  After several days of imprinting the texture of the wall on my forehead, quite a bit of research, four installation CDs,  and nearly a dozen blind alleys from very intelligent people trying to be helpful on this forum, I finally discovered my problem.  It was actually my motherboard.  Yeah, I know, you say it can't be your motherboard because Windows works just fine.  I had the same situation.  As it turns out I was running a GPU ( graphics processor ) that was in the Intel family.  Intel 950 GMA, to be specific.  Intel does a poor to non-existent job of supporting Linux with most of their graphics card, and mine happened to fall into the non-existent category.  At the end of the day I simply threw my Ubuntu drive that would not boot into an enclosure ( we're talking laptop here ), plugged it into a machine with a different GPU, and voila, I had a perfectly working Ubuntu.  Meanwhile the old machine still runs Windows like it's getting paid to do so.

I'm not saying that this is the problem in your situation.  I am simply saying that when you run out of obvious causes you'll only make yourself crazy doing the same install over and over again.  There is a reason it isn't working.  Take half a step back, stop banging your head against the wall, and look at it from a different perspective.

For reference, you can see my frustration here [http://ubuntuforums.org/showthread.php?t=1567427]("http://ubuntuforums.org/showthread.php? t=1567427") and here [http://ubuntuforums.org/showthread.php?t=1567880]("http://ubuntuforums.org/showthread.php?t=1567880"), though both of these were after the initial install drama.

---

### Post by Gunman1982 on 2010-09-11
Mh I don't know if your ide cable has three connectors but if it does you could plug in your hdd and dvd-player both in ide0 on your motherboard.

That means a speed drawback but at least you can try an install.

Another try would be to install using an usb-stick and network install (probably time consuming with your connection).

---

### Post by jtarin on 2010-09-11
Well now that your HD is working in that slot you can try a USB flash install of Ubuntu.You will have to get your CD/DVD drive working to create the USB but maybe we're close now. [Here's a link to creating the USB.]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/") You should already have the .iso of 10.04

---

### Post by amjjawad on 2010-09-11
> **ubunwhat said:**
> Hey brother, a few observations from a fellow noob who found himself well more than half way to cranial meltdown during installation less than a week ago.

For starters, as someone else suggested it really sounds as if your iso is bad.  I had this problem the first time that I tried to install Ubuntu and had to download from another source, wipe everything clean, and start over.  

Second, and this is really the part that had me talking to myself, the issue that you were getting when you did manage to get at least some piece of an installation going ( the Ubuntu screen with the five dots that look like they are doing something but actually don't ) gave me flashbacks.  After several days of imprinting the texture of the wall on my forehead, quite a bit of research, four installation CDs,  and nearly a dozen blind alleys from very intelligent people trying to be helpful on this forum, I finally discovered my problem.  It was actually my motherboard.  Yeah, I know, you say it can't be your motherboard because Windows works just fine.  I had the same situation.  As it turns out I was running a GPU ( graphics processor ) that was in the Intel family.  Intel 950 GMA, to be specific.  Intel does a poor to non-existent job of supporting Linux with most of their graphics card, and mine happened to fall into the non-existent category.  At the end of the day I simply threw my Ubuntu drive that would not boot into an enclosure ( we're talking laptop here ), plugged it into a machine with a different GPU, and voila, I had a perfectly working Ubuntu.  Meanwhile the old machine still runs Windows like it's getting paid to do so.

I'm not saying that this is the problem in your situation.  I am simply saying that when you run out of obvious causes you'll only make yourself crazy doing the same install over and over again.  There is a reason it isn't working.  Take half a step back, stop banging your head against the wall, and look at it from a different perspective.

For reference, you can see my frustration here [http://ubuntuforums.org/showthread.php?t=1567427]("http://ubuntuforums.org/showthread.php?%20t=1567427") and here [http://ubuntuforums.org/showthread.php?t=1567880](http://ubuntuforums.org/showthread.php?t=1567880), though both of these were after the initial install drama.

Hi there :)
Hahaha, I really enjoyed reading your post and I really like it.

I'm not going to through my MB away nor buy any new HW just to install Ubuntu. At the end, I'm supposed to stay away from PCs as doctors ordered me to.

I'm just trying and trying to find a solution to this problem for one good reason which is I don't have "impossible" in my dictionary ;)

Problem is and hope NO ONE will get me wrong, people sometimes don't read between the lines and I do understand why. Following with such a thread is not an easy thing, specially when your eyes sometimes can't read certain lines/words. Please, hope NO ONE will get me wrong :)
I suspected since the beginning that there's something wrong with my MB (Mother Board) but it's not a HW (Hardware) failure, it's just that my MB can't do particular stuff.

Thank you so much for sharing your experience and don't worry, I'll not hit my head against the wall, I'll do that in case my PC will die :)

---

### Post by amjjawad on 2010-09-11
> **Gunman1982 said:**
> Mh I don't know if your ide cable has three connectors but if it does you could plug in your hdd and dvd-player both in ide0 on your motherboard.

That means a speed drawback but at least you can try an install.

Another try would be to install using an usb-stick and network install (probably time consuming with your connection).

Mate, I've never heard about an IDE cable with 3 connectors :) an IDE cable should have two connectors which means you can connect 2 devices (Master and Slave). SATA Cables has one connector anyway.

I was talking about my Mother Board. It has 3 IDE slots, each could be connected to 2 IDE devices. Also, it has 2 SATA slots, each slot can could be connected to 2 SATA devices. So, My MB can handle MAX=
4 SATA devices
6 IDE devices

There's a slightly difference between IDE 0 and IDE 1 + IDE 2. Looks like there's something in IDE 0 (where my DVD driver was connected) that is not there in the other two slots (IDE 1 and IDE 2).
I know this is very complicated, I have some experience with both HW and SW and I'm not trying to make it even harder for anyone but just to share with you what do I have and what it looks like over here.

Funny thing is, I can't find my MB model in Gigabyte's website. 

I WOULD LOVE to connect my Maxtor 40GB IDE HDD with my DVD drive but that means I have to take them both out of the case and ... it's a long story. I could try that but my PC will not look good with such a mess :)
My SATA HDDs are inside, my IDE HDD is already outside, if I need to put my DVD and my IDE HDD on the same cable, it means the DVD driver should go out. The cable is not tall and the length between the sockets is short. 

The only way left as you suggested is the USB-stick.

---

### Post by Kixtosh on 2010-09-11
I liked Dave's suggestion best:

> **anewguy said:**
> ...

- my recommendation:  Using a LiveCD and running gparted, remove all partitions from your 40gig drive - do not create any after you have removed all of them.  **Completely unplug the cables going to all of your other hard drives.**  For your 40gig drive (I believe you said it's IDE?) be sure to set the BIOS so only that drive is recognized and is set as the boot device. With the LiveCD running, select install Ubuntu.  If you only have 1 disk recognized, which should be the case with the other cables removed, just let it install using all of your drive - don't do the option to define your partitions.  Let that go and see if it installs - it should - if not, stop, and post back the error messages.  If it does complete, do a restart and remove the LiveCD so it boots from the 40gig drive.  Grub will have been installed to that drive only, and will only be aware of Ubuntu.  Once this is all able to boot, the other drives can be added back in.  If you want the option to boot Windows or Linux - e.g. the grub menu, only update grub on the 40gig drive and always leave it as the boot device in the BIOS.  You'll be able to run Windows from there once grub is updated, something we can easily walk you through. ...

Just use the "use entire disk option" as he suggests, from the Live CD, and let Ubuntu have at it with your 40GB HDD as if it were the only HDD and the only O.S. on there.

Whether you decide to try this or not, or pursue the USB install option first, and as others have said: _FIRST_ check the MD5 sum of your ISO download and make sure it matches the proper number, just so that a faulty download or CD burn can be eliminated. This is so easy to do, and you can even use the Live CD and a terminal command in Ubuntu to do it, if you don't want to download the little application that allows you to do it in Windows.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The hardest part of this procedure will be figuring out where your stored the download! 


_Excerpt from that link:_ First open a terminal and go to the correct directory to check a downloaded iso file:
```
cd download_directory
```
Then run the following command from within the download directory.```
md5sum ubuntu-8.10-desktop-i386.iso
```
md5sum should then print out a single line after calculating the hash:```
24ea1163ea6c9f5dae77de8c49ee7c03 ubuntu-8.10-desktop-i386.iso
```
Compare the hash (the alphanumeric string on left) that your machine calculated with the corresponding hash on the UbuntuHashes page.

The example uses Ubuntu 8.10, but the correct number for 10.04, depending on which version you downloaded, is here:

[https://help.ubuntu.com/community/UbuntuHashes#10.04](https://help.ubuntu.com/community/UbuntuHashes#10.04) LTS

My apologies in advance if I'm not reading between the lines correctly, but my mental capacities are somewhat limited, as my wife often reminds me ;).

---

### Post by amjjawad on 2010-09-11
> **jtarin said:**
> Well now that your HD is working in that slot you can try a USB flash install of Ubuntu.You will have to get your CD/DVD drive working to create the USB but maybe we're close now. [Here's a link to creating the USB.]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/") You should already have the .iso of 10.04

Even on the old HW setup, my Maxtor HDD was working except BIOS detect and read it as SCSI and I can't install Ubuntu on it.

I have to swap again between cables so that I can use my DVD drive again.

I'm going to use the USB flash to install Ubuntu but after all what I've seen in my PC, I guess it will never work. Problem is BIOS is detecting that drive (Maxtor 40GB IDE) as SCSI and I guess this is the main issue and the main reason of all that.

You know? I was thinking to install Windows XP on Maxtor HDD but I think it's useless as long as we're talking about Ubuntu and there's no point to get Windows XP working while can't even install Ubuntu.

Sadly no one here faced the same issue with his/her PC. Perhaps I have a bit of complected setup. I mean, SATA, IDE, etc.

One more try with the USB just for you guys and thanks again for everything.

Let's see what could happen :)

---

### Post by jtarin on 2010-09-11
just one more time to assure yourself that its correct, check the jumper settings on that drive.

---

### Post by amjjawad on 2010-09-11
> **Kixtosh said:**
> I liked Dave's suggestion best:



Just use the "use entire disk option" as he suggests, from the Live CD, and let Ubuntu have at it with your 40GB HDD as if it were the only HDD and the only O.S. on there.

Whether you decide to try this or not, or pursue the USB install option first, and as others have said: _FIRST_ check the MD5 sum of your ISO download and make sure it matches the proper number, just so that a faulty download or CD burn can be eliminated. This is so easy to do, and you can even use the Live CD and a terminal command in Ubuntu to do it, if you don't want to download the little application that allows you to do it in Windows.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The hardest part of this procedure will be figuring out where your stored the download! 


_Excerpt from that link:_ First open a terminal and go to the correct directory to check a downloaded iso file:
```
cd download_directory
```Then run the following command from within the download directory.```
md5sum ubuntu-8.10-desktop-i386.iso
```md5sum should then print out a single line after calculating the hash:```
24ea1163ea6c9f5dae77de8c49ee7c03 ubuntu-8.10-desktop-i386.iso
```Compare the hash (the alphanumeric string on left) that your machine calculated with the corresponding hash on the UbuntuHashes page.

The example uses Ubuntu 8.10, but the correct number for 10.04, depending on which version you downloaded, is here:

[https://help.ubuntu.com/community/UbuntuHashes#10.04](https://help.ubuntu.com/community/UbuntuHashes#10.04) LTS

My apologies in advance if I'm not reading between the lines correctly, but my mental capacities are somewhat limited, as my wife often reminds me ;).



The main reason why I didn't reply him or take his suggestion is because my main HDD is a bit crazy/faulty and I might lose it again like what happened with me few months ago. I wrote that already before, that's why I was talking about "between the lines" thing :)
Hahaha, don't worry if you couldn't read that, I do that myself so forget it :)


[http://i53.tinypic.com/1yn2p3.jpg](http://i53.tinypic.com/1yn2p3.jpg)

They're the same. I just did that by the way and didn't do it earlier. Why? because when I tried my old Ubuntu 9.10 CD, it didn't work and gave the same error msg. My 9.10 CD was working and I managed to install Ubuntu 9.10 perfectly fine a year ago (the time I joined here first) and at that time, I've never heard about MD5 sum and stuff like that :)
As I said, I have good experience with PCs and IT in general so I eliminate the slim chances and take the big/fat one :P

So, now, everyone is 100% sure there's NOTHING wrong with my ISO file :)

I'll just give it one more try with USB-Stick, that's all what I could do for now.

Thanks a lot, buddy :)

---

### Post by Gunman1982 on 2010-09-11
> **amjjawad said:**
> Mate, I've never heard about an IDE cable with 3 connectors :) an IDE cable should have two connectors which means you can connect 2 devices (Master and Slave). SATA Cables has one connector anyway.


Well I guess I was misunderstood ... IDE cable come with either 2 connectors or 3, meaning 
Mobo -> Device (2 connector)
Mobo -> Device-1 /Device-2 (3 connector)
If I would have said two connector I was afraid that it sounded like the first option. Maybe I should have asked for a cable for 2 devices.
Anyway, did you already try the other 2 ide slots?

Normally the first one (ide0 or 1 however you want to name it) is of different type which supports higher bandwidth (called UDMA) you need to have a special cable for that though (80 instead of 40 lines).

---

### Post by anewguy on 2010-09-11
> **amjjawad said:**
> Negative. If it's a faulty RAM, then the whole PC will not even turn on ;)

Again, this isn't true unless a very hard failure.  You can weak gates internal to the chips, etc., so that data isn't clocked to the bus correctly part of the time, bits are flipped part of the time, etc..

---

### Post by MasterNetra on 2010-09-11
> **amjjawad said:**
> The only option I got or can do is "delete" the partition using Windows Disc Management (I got two partitions by the way which have been set by Ububtu during installation) but I'm not quite sure whether it's advisable to "delete" these two partitions or not?

If this was answered already then my apologies I must of missed that post, but one partition would be the one Ubuntu would be on, and the second is Linux swap, both are expendable so feel free to delete them both. The Linux swap will be the smaller of the two. I usually get it at around 2GB of size on my system and have 1GB of ram, so at 2GB it might be at 4GB. The size regardless will most certainly give it away.

---

### Post by anewguy on 2010-09-11
The reason I suggested disconnecting all your other drives (yes, I DID read your posts and knew you didn't want to powerdown in case your "iffy" main drive failed) was because you are spinning your wheels without truely troubleshooting the problem.  If you install Ubuntu you would at least stand a chance of recovering data from your "iffy" main drive before it completely fails.  Removing a potentially failing drive from the mix (is it the drive, is the cable, is it the controller on the MB, is it the socket on the Mb?? - you get the idea) helps eliminate 1 source of problems.

I know you swear your CD is okay, but believe everyone when they are telling you what to do - there have been TONS of posts here where people didn't check the md5 sum, didn't burn at the lowest speed, etc., and guess what?  Problems similar to yours - works in 1 PC but not in another.  It's a matter of age of drive, how aligned the heads are from one drive to another, if the read heads are failing just a little, etc.   People aren't trying to hassle you here, and you need to quit blowing off some suggestions just because you think you know better.  You wouldn't be asking for help if you did.

---

### Post by MasterNetra on 2010-09-11
> **amjjawad said:**
> Even on the old HW setup, my Maxtor HDD was working except BIOS detect and read it as SCSI and I can't install Ubuntu on it.

I have to swap again between cables so that I can use my DVD drive again.

I'm going to use the USB flash to install Ubuntu but after all what I've seen in my PC, I guess it will never work. Problem is BIOS is detecting that drive (Maxtor 40GB IDE) as SCSI and I guess this is the main issue and the main reason of all that.

You know? I was thinking to install Windows XP on Maxtor HDD but I think it's useless as long as we're talking about Ubuntu and there's no point to get Windows XP working while can't even install Ubuntu.

Sadly no one here faced the same issue with his/her PC. Perhaps I have a bit of complected setup. I mean, SATA, IDE, etc.

One more try with the USB just for you guys and thanks again for everything.

Let's see what could happen :)

Also you could download  UNebootin and install the Ubuntu iso into the USB Drive with that, there is a windows version of it, and its portable, by which I mean you just run that one .exe to run the app. Though I forget if UNetbootin sets the boot flag for the USB Drive's Partition or not...

---

### Post by amjjawad on 2010-09-11
> **jtarin said:**
> just one more time to assure yourself that its correct, check the jumper settings on that drive.

I'm using the USB to install but I was just wondering if what I did is correct or wrong?

[http://i51.tinypic.com/29xvl3m.jpg](http://i51.tinypic.com/29xvl3m.jpg)

As per the above screen shot, there's some options to choose where to install the boot loader.
Instead of the default option as per the screen shot (which is /dev/sda), I changed that and chose:

/dev/sdc

sdc is Maxtor 40GB IDE HDD. Where I was trying to install Ubuntu since all this hassle started.

So, hope I didn't do anything wrong regarding the boot loader option (as per the screen shot - [http://i51.tinypic.com/29xvl3m.jpg](http://i51.tinypic.com/29xvl3m.jpg) ).

Thank you!

---

### Post by amjjawad on 2010-09-11
> **MasterNetra said:**
> If this was answered already then my apologies I must of missed that post, but one partition would be the one Ubuntu would be on, and the second is Linux swap, both are expendable so feel free to delete them both. The Linux swap will be the smaller of the two. I usually get it at around 2GB of size on my system and have 1GB of ram, so at 2GB it might be at 4GB. The size regardless will most certainly give it away.

That's a very old issue now, we got a lot more :P hehe

Never mind, just forget about that one and thanks a lot for helping :)

---

### Post by amjjawad on 2010-09-11
> **anewguy said:**
> The reason I suggested disconnecting all your other drives (yes, I DID read your posts and knew you didn't want to powerdown in case your "iffy" main drive failed) was because you are spinning your wheels without truely troubleshooting the problem.  If you install Ubuntu you would at least stand a chance of recovering data from your "iffy" main drive before it completely fails.  Removing a potentially failing drive from the mix (is it the drive, is the cable, is it the controller on the MB, is it the socket on the Mb?? - you get the idea) helps eliminate 1 source of problems.

I know you swear your CD is okay, but believe everyone when they are telling you what to do - there have been TONS of posts here where people didn't check the md5 sum, didn't burn at the lowest speed, etc., and guess what?  Problems similar to yours - works in 1 PC but not in another.  It's a matter of age of drive, how aligned the heads are from one drive to another, if the read heads are failing just a little, etc.   People aren't trying to hassle you here, and you need to quit blowing off some suggestions just because you think you know better.  You wouldn't be asking for help if you did.

WOW, easy anewguy! I feel that you're shouting in my ears directly! cool down, please, ok?
I'm not showing off or something when I'm writing "I know ...". Are we clear? good!

First thing first, I do appreciate your help and others' help as well. One of the reasons why I want Ubuntu is because of this great forum, period :)

Secondly, if I disagree with someone (because simply I know more about my PC - obviously) it doesn't mean I'm not accepting his/her help, right? :)

It's NOT true that I'm spinning my wheels without solving/troubleshooting the problem, but as I said, I'm putting all the info I have here so that you guys could help. That's all. And again, I do understand that whatever I write here, still there's some missing facts. What I mean is, you can't describe everything here because that would take ages. All what you need to do is write down the important stuff. I admit that I put lots of info that created a confusion, sorry about that but I'm very new to this forum. I joined last year and after one year I'm back. Anyway, let's stop that because we're changing the topics here :)

[COLOR=Red]"If you install Ubuntu you would at least stand a chance of recovering  data from your "iffy" main drive before it completely fails."[/COLOR]
As I have written since the beginning of this topic, I'm installing Ubuntu on my IDE HDD which is 40GB. My main HDD (as I wrote before too) is SATA so obviously the size of SATA HDD is much more than the size of IDE HDD. Just FYI, my iffy HDD size is 160GB. ALL what I care about that drive is it's the only way I can connect to the internet as this is my only PC. If I'll lose that drive (SATA 160GB), how would I login here? hope you understand now.

And yes, it could help when my Maxtor 40GB is SATA but it's not and my BIOS is detecting it as SCSI which is the source or the problem. I'll explain that soon!

If you check my previous posts, you'll understand that I did that MD5 sum and the .iso file is perfect.
[http://i53.tinypic.com/1yn2p3.jpg](http://i53.tinypic.com/1yn2p3.jpg)

Finally, YES, I would not ask for help if I know how to fix that problem ;)

Peace!

---

### Post by amjjawad on 2010-09-11
> **MasterNetra said:**
> Also you could download  UNebootin and install the Ubuntu iso into the USB Drive with that, there is a windows version of it, and its portable, by which I mean you just run that one .exe to run the app. Though I forget if UNetbootin sets the boot flag for the USB Drive's Partition or not...

Already did but mission failed. I'll explain in a new post!

---

### Post by amjjawad on 2010-09-11
> **amjjawad said:**
> Even on the old HW setup, my Maxtor HDD was working except BIOS detect and read it as SCSI and I can't install Ubuntu on it.

I have to swap again between cables so that I can use my DVD drive again.

I'm going to use the USB flash to install Ubuntu but after all what I've seen in my PC, I guess it will never work. Problem is BIOS is detecting that drive (Maxtor 40GB IDE) as SCSI and I guess this is the main issue and the main reason of all that.

You know? I was thinking to install Windows XP on Maxtor HDD but I think it's useless as long as we're talking about Ubuntu and there's no point to get Windows XP working while can't even install Ubuntu.

Sadly no one here faced the same issue with his/her PC. Perhaps I have a bit of complected setup. I mean, SATA, IDE, etc.

One more try with the USB just for you guys and thanks again for everything.

Let's see what could happen :)


As I suspected, it happened that my guess was right and I feel so sad because of this :(

I have good news and bad news. Good news is: I managed to install Ubuntu using the USB-Stick. Bad news is, when I returned everything to its last setup (my DVD driver on IDE 0 slot and my Maxtor 40 GB IDE on IDE 1 slot), Ubuntu stopped working :(

The main reason of this (as I was concerned about) is the BIOS. No, it's not faulty but looks like my MB (mother board) reads whatever device attached to IDE 1 and IDE 2 as SCSI. It stops reading my Maxtor 40GB IDE HDD as SCSI once I install it on IDE 0.

You know when you turn your PC ON, when it gives you the info about your RAM and CPU, also a list of your drivers? usually, my Maxtor HD is not listed in that list, it's listed in another page actually. ALL what I got in the first list (exactly under CPU Speed and RAM) is:
1- My main SATA HDD - Master
2- My 2nd SATA HDD - Slave
3- My DVD Drive
4- None.

And NO, unfortunately, I can't install my Maxtor HDD as a slave/master with my DVD drive :( I don't have space in my case. I'm putting my Maxtor HDD outside the case. If you just look at it, my case looks so funny indeed. It's like an external one but linked with IDE cable. I guess I need bigger case with 4 slots to install the HDDs.

Anyway, above all, I can't get rid of this menu:

[COLOR=Blue][B]Windows Boot Manager

Windows 7
Ubuntu

Tools: Windows Manager Diagnostic [/B][/COLOR] 

I guess someone said it's GBRU2 or something? sorry if I misspelled it. 

Dammit, this is really crazy!

---

### Post by jtarin on 2010-09-11
That's not Grub2 that's the Win7/Vista Loader you see. Have you researched why your bios sees an IDE as a SCSI...maybe it's not a problem but it's for Bios Compatibility with SATA. I'm only guessing here.

---

### Post by amjjawad on 2010-09-11
> **jtarin said:**
> That's not Grub2 that's the Win7/Vista Loader you see. Have you researched why your bios sees an IDE as a SCSI...maybe it's not a problem but it's for Bios Compatibility with SATA. I'm only guessing here.

I'll post here few screen shots that will help everyone to understand my problem even better. Pictures always describe better than words.

>> This screen shot for my BIOS disc priority

[http://i53.tinypic.com/2lcfns.jpg](http://i53.tinypic.com/2lcfns.jpg)

It shows how the BIOS detect the Maxtor 40G IDE HDD as SCSI. That's the main reason, actually the only reason why I can't install and use Ubuntu on my machine


>> This screen shot for what I got once I turn my PC on. It shows clearly what's going on and how my machine is detecting my devices.

[http://i52.tinypic.com/2zivt78.jpg](http://i52.tinypic.com/2zivt78.jpg)




So, after all this, is there any hope that we could solve this issue?
Also, is there any way I could remove this boot loader Menu? 

I tried to search why my BIOS detect my Maxtor HDD as SCSI but couldn't find similar issue.

---

### Post by jtarin on 2010-09-11
You will see two screens they are clearly marked. Now there should be no doubt. Which one is yours?

---

### Post by jtarin on 2010-09-11
[Some information about SCSI so you will know what your dealing with and how to solve it]("http://www.wisegeek.com/what-is-scsi.htm").

---

### Post by amjjawad on 2010-09-11
> **jtarin said:**
> You will see two screens they are clearly marked. Now there should be no doubt. Which one is yours?

I already posted the screen shots on my previous post.

Anyway, I'm going to post it again.

This is exactly what I got: [http://i54.tinypic.com/sl4kxv.jpg](http://i54.tinypic.com/sl4kxv.jpg)

---

### Post by Kixtosh on 2010-09-11
Looks a whole lot like the Windows Boot Manager to me, NOT GRUB (and I saw it the first time, by the way).

---

### Post by amjjawad on 2010-09-11
> **Kixtosh said:**
> Looks a whole lot like the Windows Boot Manager to me, NOT GRUB (and I saw it the first time, by the way).

Yes, I just checked Windows 7 and you're absolutely right. I'm sorry, I thought it's GRUB2.

I need to figure out how to remove that option but that's not a big deal now, I want to know whether I'm going to have this Ubuntu up and running or should I go to bed and have some sleep? :)

I need to find out WHY my BIOS is detecting the IDE HDD as SCSI.
The screen shots on my previous post show everything.

Thank you :)

---

### Post by amjjawad on 2010-09-11
> **jtarin said:**
> [Some information about SCSI so you will know what your dealing with and how to solve it]("http://www.wisegeek.com/what-is-scsi.htm").

I really appreciate that but it doesn't seem to help to fix my problem. I read what they say. No worries, I'll try to google it and see.

Thanks a lot :)

---

### Post by luceerose on 2010-09-11
> **mastablasta said:**
> Mistake no. 1: you are using Wubi. 

Bingo.
Boot to the installation disc & install without using Wubi.

---

### Post by jtarin on 2010-09-11
He can't boot to the drive...read the entire thread.

---

### Post by amjjawad on 2010-09-12
I was searching on google to find a similar scenario of mine. Honestly, did not find an exact case but I found almost similar cases but in all these cases, one of the devices wasn't readable/accessible (in my case, the IDE HDD is accessible but BIOS detects it as SCSI). Also, most of the threads I found were old and without solutions :(

From what I understood, this is a common issue when a PC has both SATA and IDE HDDs/Devices.

Ok, at least, I know what I'm looking for now. I'll try to find the best settings/configurations for BIOS to manage multiple HDDs (SATA and IDE) in the same time.


Also, I unplugged the power and the data cable from my SATA HDDs last night but that didn't solve the problem, BIOS still reading/detecting my Maxtor HDD as SCSI. Also, I played around with the BIOS settings (Auto, Enhanced, Combined, Non-Combined) but same result, BIOS can only read my Maxtor 40GB HDD as SCSI.

I was trying to find something in the MB manual but nothing is there.

Will keep searching... this issue took so much time to get resolved!
The good thing is, I'm learning lots of stuff with each search :)

---

### Post by jtarin on 2010-09-12
Is your IDE plugged into a SCSI controller card.If you were to disconnect and plug directly to motherboard I think t would solve your SCSI detection.

---

### Post by elliotn on 2010-09-12
its better to format the HD with a windows CD. it should say unknown partition and only give u the delete option,  just follow it and delete it then format it, then u can start again, check your ISO if it is has no errors

---

### Post by amjjawad on 2010-09-12
> **jtarin said:**
> Is your IDE plugged into a SCSI controller card.If you were to disconnect and plug directly to motherboard I think t would solve your SCSI detection.

After ALL what I've written over here, you still think I do have a SCSI controller?

WHY it's so hard for people to read and understand? am I using simple English guys!

I think I have to take a picture to my Case and MB and everything so that people can understand what I do have.

NO, I don't have a SCSI control. Do you think I would forget to mention that since the beginning?

Sorry if this sounds rude but I'm really tired of keep explaining the same thing over and over again!

---

### Post by elliotn on 2010-09-12
its better to format the HD with a windows CD. it should say unknown partition and only give u the delete option,  just follow it and delete it then format it, then u can start again, check your ISO if it is has no errors

---

### Post by jtarin on 2010-09-12
Do you think this is the only topic I spend my time on? Are you helping x number of people and trying to keep a complete list of ten pages or more of hardware and software discussion in your head with people that have no clue to there problem. I'm not sitting in front of your computer, you are. I'm sorry if I ask you to answer questions that have been asked.Have a nice day.

---

### Post by amjjawad on 2010-09-12
> **jtarin said:**
> Do you think this is the only topic I spend my time on? Are you helping x number of people and trying to keep a complete list of ten pages or more of hardware and software discussion in your head with people that have no clue to there problem. I'm not sitting in front of your computer, you are. I'm sorry if I ask you to answer questions that have been asked.Have a nice day.


Please accept my apology. I was so frustrated and upset not at you but at myself because this is the first time I can't solve a PC-Problem. I used to fix such stuff on the spot but looks like I'm getting rusty/old.

Sorry again, I understand it's SO HARD to keep track on everyone's problem. Hope you understand my frustration.

You've been a great support indeed.

---

### Post by amjjawad on 2010-09-12
> **elliotn said:**
> its better to format the HD with a windows CD. it should say unknown partition and only give u the delete option,  just follow it and delete it then format it, then u can start again, check your ISO if it is has no errors

Already done many times before 3 days or more but nothing happened.

Thanks for the help :)

---

### Post by amjjawad on 2010-09-12
Ok, so apparently, I got some help from outside this forum after hours of digging and searching.
I'd like to share this with EVERYONE here.

[http://www.computing.net/answers/hardware/my-bios-is-driving-me-crazy-please-help/69471.html](http://www.computing.net/answers/hardware/my-bios-is-driving-me-crazy-please-help/69471.html)

_**I'd like to show my appreciation for ALL those who tried to help and waste so much time trying to figure out how to fix my problem. Thanks a lot :)**_

---

### Post by amjjawad on 2010-09-12
As for Ubuntu, I installed my HDD on IDE CH1 (Master) along with the DVD Drive (Slave) but both devices are outside my case/tower until I buy that adapter as explained in the previous post.

My main SATA HDD is dying or it could be dead. Because I had to turn my PC off, it looks like it stopped working as it happened before few months ago.
My tower looks so naked and it doesn't look nice at all so I have to put everything to its place soon.

So far, Ubuntu is working AS LONG AS my BIOS is detecting my Maxtor 40GB IDE HDD as an IDE drive NOT as SCSI. If I'll go back to the previous setup/config, then it would stop working immediately.

I can't find Gparted, not sure why but it shouldn't be a problem, I guess I can download it beside I don't really need it.

As for Windows 7, it's gone as long as my main SATA HDD is not working :(
So, the only OS I do have right now is Ubuntu.

Will keep this thread open in case something wrong could happen and will mark it SOLVED if everything is ok.

Once more, thank you ALL for everything ;)

---

### Post by anewguy on 2010-09-13
> **amjjawad said:**
> WOW, easy anewguy! I feel that you're shouting in my ears directly! cool down, please, ok?
I'm not showing off or something when I'm writing "I know ...". Are we clear? good!
Just another example of the attitude I'm talking about.

> First thing first, I do appreciate your help and others' help as well. One of the reasons why I want Ubuntu is because of this great forum, period :)

Secondly, if I disagree with someone (because simply I know more about my PC - obviously) it doesn't mean I'm not accepting his/her help, right? :)

If you knew THAT much about your PC, you wouldn't say some of the things you say.


> It's NOT true that I'm spinning my wheels without solving/troubleshooting the problem, but as I said, I'm putting all the info I have here so that you guys could help. That's all. And again, I do understand that whatever I write here, still there's some missing facts. What I mean is, you can't describe everything here because that would take ages. All what you need to do is write down the important stuff. I admit that I put lots of info that created a confusion, sorry about that but I'm very new to this forum. I joined last year and after one year I'm back. Anyway, let's stop that because we're changing the topics here :)
Nobody's changing topics - this is all trying to deal directly with your problem and what comes across as attitude.  Perhaps you are from another culture, and therefore how you phrase somethings is okay to you, but not here.  You seem to be always talking negatively everytime someone offers help.
> [COLOR=Red]"If you install Ubuntu you would at least stand a chance of recovering  data from your "iffy" main drive before it completely fails."[/COLOR]
As I have written since the beginning of this topic, I'm installing Ubuntu on my IDE HDD which is 40GB. My main HDD (as I wrote before too) is SATA so obviously the size of SATA HDD is much more than the size of IDE HDD. Just FYI, my iffy HDD size is 160GB. ALL what I care about that drive is it's the only way I can connect to the internet as this is my only PC. If I'll lose that drive (SATA 160GB), how would I login here? hope you understand now.
First, please don't try to "preach" to me about IDE versus SATA and the different sizes of your drives. First off, you're talking to someone who already knows, second, just removing your other drives from the mix and having your CD and the 40gig IDE drive hooked up is good troubleshooting, in that it eliminates other potentials for problems - anything that goes wrong would then have to be directly in that chain.  IDE versus SATA doesn't have a dang thing to do with that testing.  Also, how the heck do you think you can change cables, etc., without powering the machine down - same risk there as with my suggestion - SATA can be hot-swap, but I've never known an IDE that could (not saying it's not possible, but I have never in 35+ years of experience seen one).

> And yes, it could help when my Maxtor 40GB is SATA but it's not and my BIOS is detecting it as SCSI which is the source or the problem. I'll explain that soon!

If you check my previous posts, you'll understand that I did that MD5 sum and the .iso file is perfect.
[http://i53.tinypic.com/1yn2p3.jpg](http://i53.tinypic.com/1yn2p3.jpg)

Finally, YES, I would not ask for help if I know how to fix that problem ;)

Peace!

Lotsa luck

---

### Post by anewguy on 2010-09-13
> **amjjawad said:**
> Ok, so apparently, I got some help from outside this forum after hours of digging and searching.
I'd like to share this with EVERYONE here.

[http://www.computing.net/answers/hardware/my-bios-is-driving-me-crazy-please-help/69471.html](http://www.computing.net/answers/hardware/my-bios-is-driving-me-crazy-please-help/69471.html)

_**I'd like to show my appreciation for ALL those who tried to help and waste so much time trying to figure out how to fix my problem. Thanks a lot :)**_

You did notice that all they were talking about there are the simple 3 1/2 to 5 1/4 screw on drive adapters?  Why would this be NEW to you if you know so dang much and have so much experience?

This is another example of (a) either a very lost translation from another culture or (b) a real attitude problem.

These adapters are old hat.  So are IDE to SATA adapters.  Don't understand why this was all new to you.

---

### Post by anewguy on 2010-09-13
> **amjjawad said:**
> After ALL what I've written over here, you still think I do have a SCSI controller?

WHY it's so hard for people to read and understand? am I using simple English guys!

I think I have to take a picture to my Case and MB and everything so that people can understand what I do have.

NO, I don't have a SCSI control. Do you think I would forget to mention that since the beginning?

Sorry if this sounds rude but I'm really tired of keep explaining the same thing over and over again!

Another example of a REAL attitude problem.  People are trying to help, you think you know more, you bark at them or do your little condescending "ha-ha" remark.  

Grow-up, take some criticism, take people as trying to help (remember, EVERYONE is volunteering here).  You maintain this in any future threads and you are quite likely to find that people won't be as willing to help.  Think you know better?  Well, TRY being humble - you might get a lot further.

As far as explaining over and over, obviously you haven't done that great of job or people would not be asking the questions you seem to find so offensive.  

When posting here, break your problem down to it's most simplest form.  Additional details can be added as needed when asked.

I also noticed that your post says you just have the 40-gig drive and the CD drive attached and Ubuntu is working as long as you have the IDE cable connected to the "correct" channel on the motherboard.  Isn't this what I suggested and that you blew off because you knew better????

<snip>

Harsh words?  You bet.  Take them to heart?  I hope you do.

BTW - to save you and anyone else the trouble, I'm reporting myself, so to use your words "ha-ha".

---

### Post by amjjawad on 2010-09-13
anewguy,

Thanks a lot for this amazing lecture :)

Have a nice day!

---

### Post by ginger_fury on 2010-09-13
hi all
 
i'm trying to follow this as i have what i think is a similar problem...
 
i tried to install ubuntu 10.4 over the top of windows (deleting it) and got the same hard drive error that then caused the installation to stop.
 
now when i switch on the laptop, after pressing f1 (annoying), i just get the ubuntu logo and can't get beyond this...(i tried a different/slowly burnt ubuntu disc - no joy)
 
please help...
 
 
(i apologise if this has already been mentioned but following this thread was a bit difficult and it began degenerating)

---

### Post by mastablasta on 2010-09-13
> **ginger_fury said:**
> 
 
 after pressing f1 (annoying),)
 
why do you need to perform this act? also i think it would be better to create another thread unless your bios is saying you have SCSI disk while you actually have IDE.

---

### Post by perspectoff on 2010-09-13
> **amjjawad said:**
> Hi everyone,

Well, this is a bit weird and I'm not sure what's going on so hopefully someone does and could help me out!

Let me first tell you what kind of PC/configuration I do have:
I have a desktop PC (P4) with 2GB of RAM, two SATA HDDs, one IDE HDD (40GB), Windows 7 on HD1 (SATA). I had some hard time to download Ubuntu (download failed in the process) so finally I decided to use torrent to get it. I burned the iso image to a blank CD and started Wubi to install Ubuntu 10.04 on my**_ 40GB IDE HDD_**. 

Wubi started to install files, for some reason my CD got ejected (not sure why) and Wubi asked me either to restart now or do it manually later. I chose to restart now without the CD (I thought it doesn't require a CD as it got ejected). When nothing happened, I put the CD back and restart my PC. So far, so good.

When the installation steps appeared, I chose my location, language, etc and then I chose:
**Erase and use the entire disc** in step 4 and of course I chose my [B][U]40GB IDE HDD.
[/U][/B]The last step I did in the installation wizard was choosing the loader to be from my [B][U]40GB IDE HDD and I'm afraid that caused the problem.

[/U][/B]Now, what happened is: suddenly, I got an error message, not sure what exactly it said but in general, it said that my HD is either too old or damaged and need to be replaced, then the installation process stopped working or ended.
I restarted, there was an option to choose between Windows or Ubuntu but nothing happened with I chose Ubuntu.
When I booted from Windows 7, I couldn't find my [B][U]40GB IDE HDD and it's gone/missing :(
[/U][/B]I tried to reboot from the CD (ubuntu 10.04) many times but all what I got is the Ubuntu logo in the middle with 5 dots and it seems something is loading but nothing happens. I was waiting for 15mins or more but still, nothing.

All what I can do is boot from Windows 7. Everything is fine with Windows, I have no problem but I can't get my **_40GB IDE HDD _**back, can't boot from ubuntu nor can install it again.

I'm not sure whether it was my mistake from the beginning to choose Wubi or it was my mistake when I changed the loader option? not sure what's going on.

I tried to search the forum for similar issue but I couldn't find one.

Is there someone who could possibly help me, please?
I need my [B][U]40GB IDE HDD back and I want to install Ubuntu.
[/U][/B]If something wrong with my configuration or anything, please let me know.

Thanks a lot!

These same symptoms will happen if you have an integrated Intel graphics card on your computer, or a nVidia graphics card. (Maybe 1/3 of problems on Ubuntu forums are related to this.) Check the graphics of your computer and then hunt around for solutions particular to your graphics card.

Most people check everything else, first, but I doubt it has anything to do with your hard drive.

However, about 1/10 of my downloaded .iso images of Ubuntu have been corrupt, no matter whether I download them directly or by Torrent. I don't have any idea why, but when I download and burn them a second time they work. But look for the graphics problem, first.

---

### Post by amjjawad on 2010-09-13
Okay, this is really too much ... either I lost all my mind or there's something wrong in Ubuntu?
You know what guys? I'll forget whatever I've learned about Computers from personal experience and will start from ZERO as this is totally new to me. With Windows, I've never had such problems whatsoever!!!!!

There you go!

Everything was extra perfect last night and this morning. Afternoon, I decided to return everything to its place (*those who have been following up with this thread, will understand what I mean*) which means I had to return my Maxtor IDE 40GB HDD to its place and same for the DVD Drive as both were outside my tower/case. Why is that? because simply my main SATA WD HDD is DEAD :'( that's it, it won't work anymore (*there was tick-tick sounds months ago, I took it off and put it somewhere, I decided to check it recently and it was working fine until I had to turn my PC on and off for 100 times for the last 3 days so it passed away*. Tick-tick sounds came back without stop and I've tried my best to get it work but nothing happened).

What happened is, I tried to check whether Ubuntu will boot up if I connected my Maxtor 40G IDE HDD (***this is where Ubuntu installed***) to another IDE channel **[COLOR=Navy][ I have 4 SATA Channels - SATA 0, SATA 1, SATA 2 and SATA 3] + [ I have 3 IDE Channels - IDE Channel 1, IDE Channel 2 and IDE Channel 3][/COLOR]** and the MB is Gigabyte.

Yesterday, when I installed Ubuntu and it worked, my Maxtor 40G IDE HDD was connected to IDE Channel 1. Today, I connected it to IDE Channel 2 and yes, same hassle, BIOS detected it as SCSI ([http://i53.tinypic.com/2lcfns.jpg](http://i53.tinypic.com/2lcfns.jpg)) so I turned my PC off and installed my Maxtor 40G IDE HDD to IDE Channel 1 where BIOS detect it as IDE and everything should be fine. So far so good. 

I turned my PC on, couldn't boot from Ubuntu AT ALL. I've tired everything you can imagine but absolutely nothing. I even unplugged every other device (my 2nd SATA HDD and DVD Drive) so that my Maxtor 40G IDE HDD will be the only HDD/device installed on my MB but still, NOTHING.
Above all, when I tired to put my USB-Stick to install Ubuntu again, I couldn't do that. ALL what I get is either lots of codes/info and there's something start with "**init**" like that (init .....) but I forgot the word (sorry) OR Ubuntu logo with the dark purple background with the 5 flashing dots. I left my PC for 1 hour doing that (flashing dots) and still no response. 

Now, I've tried again but the only way I managed to boot from my USB-Stick and access the Internet and write here is:

1- I unplugged ALL the devices from the MB
2- Plugged an external HDD to USB port
3- Booted from the USB-Stick (the same one I used to install Ubuntu yesterday)
4- And here I'm able to access the forum BUT without my Maxtor 40G IDE HDD.

I hope it's clear so far.

[COLOR=Navy][B]Summary: my Maxtor 40G IDE HDD has Ubuntu just installed yesterday and I was able to login this morning, afternoon, NOTHING at all. The worst part that I don't ever understand is I CAN NOT even install Ubuntu again using my USB-Stick.
I got the Menu where it says:
1- Run Ubuntu from this USB
2- Install Ubuntu
3- Boot from the first HD

But when I choose all the above options, same dark purple background with Ubuntu's logo and the 5 amazing flashing dots![/B][/COLOR]


By the way, I can not install Windows nor Ubuntu on my 2nd SATA HDD because simply it's all what I got now with ALL my data. I can't take the risk of losing more stuff.
My External HD is 20GB. It's an internal HD and I put it in a HardBox so that I can use it as an external HD.


Is there any chance that I might get my Maxtor 40G IDE HDD working again with Ubuntu or what shall I do now?

THANKS A LOT!

---

### Post by amjjawad on 2010-09-13
> **ginger_fury said:**
> hi all
 
i'm trying to follow this as i have what i think is a similar problem...
 
i tried to install ubuntu 10.4 over the top of windows (deleting it) and got the same hard drive error that then caused the installation to stop.
 
now when i switch on the laptop, after pressing f1 (annoying), i just get the ubuntu logo and can't get beyond this...(i tried a different/slowly burnt ubuntu disc - no joy)
 
please help...
 
 
(i apologise if this has already been mentioned but following this thread was a bit difficult and it began degenerating)


Hi,

First of all, are you installing Ubuntu on a Laptop or a PC?
In both cases, could you please list your devices and configuration?

I've been through this hassle for 4 days and I feel like I'm eating, drinking and breathing Ubuntu!!!

P.S.
Why do you have to press F1???

---

### Post by jtarin on 2010-09-13
[Maxblast]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=MaxBlast_5&vgnextoid=7add8b9c4a8ff010VgnVCM100000dd04090aRCRD")

---

### Post by amjjawad on 2010-09-13
> **jtarin said:**
> [Maxblast]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=MaxBlast_5&vgnextoid=7add8b9c4a8ff010VgnVCM100000dd04090aRCRD")

Thanks a lot, mate :)

Don't hate me but the manual is more than 50 pages so what exactly I'm looking for? What Maxblast could do to solve my problem?
I don't mind to read it but I just want to know what exactly it could help?

Note that, I don't have access to my Maxtor 40GB IDE HDD and I can't run Ubuntu when I plug the power and the data cable and boot from it. It doesn't boot at all.
I'm writing now to you while I'm on the Live USB so Ubuntu is not even installed on my PC.

Many thanks!

---

### Post by jtarin on 2010-09-13
> **amjjawad said:**
> Thanks a lot, mate :)

Don't hate me but the manual is more than 50 pages so what exactly I'm looking for? What Maxblast could do to solve my problem?
I don't mind to read it but I just want to know what exactly it could help?

Note that, I don't have access to my Maxtor 40GB IDE HDD and I can't run Ubuntu when I plug the power and the data cable and boot from it. It doesn't boot at all.
I'm writing now to you while I'm on the Live USB so Ubuntu is not even installed on my PC.

Many thanks!The **Download MaxBlast** link not the .pdf...do I have to take you by the hand everywhere. Haven't you ever heard of Maxblast? and you have a Maxtor hard drive.Its aprogram of tools to use with your Maxtor drive. I would have thought it would have been the first thing you tried. Read the manual if you want or not.....its your choice.

---

### Post by amjjawad on 2010-09-13
> **jtarin said:**
> The **Download MaxBlast** link not the .pdf...do I have to take you by the hand everywhere. Haven't you ever heard of Maxblast? and you have a Maxtor hard drive.Its aprogram of tools to use with your Maxtor drive. I would have thought it would have been the first thing you tried. Read the manual if you want or not.....its your choice.

I've never had to use it nor any other "tools" because simply this is **THE FIRST TIME** I have such issue, period.

Thanks for taking my hand everywhere!

---

### Post by jtarin on 2010-09-13
In the days past Maxtor always shipped a copy with every hard drive they sold. It's worth exploring and using.

---

### Post by amjjawad on 2010-09-13
> **jtarin said:**
> [Maxblast]("http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=MaxBlast_5&vgnextoid=7add8b9c4a8ff010VgnVCM100000dd04090aRCRD")

This program works under Windows and I couldn't find any other OS that this program does support so that I could use it.
I don't have Windows, I don't have anything except a TRY Ubuntu from a USB-Stick.
To create a bootable CD/DVD, there must be Windows OS which I don't have.
This program doesn't allow you to create a bootbale USB.
I can't use this program/tool whatsoever!

Again, thanks for taking the time to read every post of mine!

---

### Post by amjjawad on 2010-09-13
> **jtarin said:**
> In the days past Maxtor always shipped a copy with every hard drive they sold. It's worth exploring and using.

Where I got this old HDD from, they don't give such a thing with it. If they have done it, I would keep it for sure. Where I live right now, they don't provide such tools when you buy a new HDD. If I ever faced such issue before, I would keep a copy (CD/DVD) a side in case of emergency. Above all, if I knew all this will happen to me, I would never ever install Ubuntu in my whole life. 
Yes, it's good experience and a chance to learn new stuff but I've been "almost" without a working PC for 4 days or more! I couldn't touch Photoshop and use it for a week and I can't live without using Photoshop. Lots of stuff I do on my PC I can't do. I know that's my problem and it's no one's else fault but I'm just saying.

---

### Post by Gunman1982 on 2010-09-13
> **amjjawad said:**
> 
What happened is, I tried to check whether Ubuntu will boot up if I connected my Maxtor 40G IDE HDD (***this is where Ubuntu installed***) to another IDE channel **[COLOR=Navy][ I have 4 SATA Channels - SATA 0, SATA 1, SATA 2 and SATA 3] + [ I have 3 IDE Channels - IDE Channel 1, IDE Channel 2 and IDE Channel 3][/COLOR]** and the MB is Gigabyte.

Is there any chance that I might get my Maxtor 40G IDE HDD working again with Ubuntu or what shall I do now?


Well I just have a guess here, not really a solution. Ubuntu identifies the partitions through the uuid, I guess that is generated by the device and probably the oder the system recognizes them (wild guess here, so rather google for that). Question is did you get the grub menu which let you choose ubuntu? Did you even have the grub menu?

---

### Post by cariboo on 2010-09-13
There is so much conflicting information in this thread, I doubt it will ever get solved. I would suggest starting a new thread. 

To the op, please provide the information the people that are trying to help ask you for. If you don't know how to provide the information, just ask and some one will walk you through the process. This thread is closed.

---

