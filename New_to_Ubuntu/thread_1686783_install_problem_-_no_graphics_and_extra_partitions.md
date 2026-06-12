---
title: "install problem - no graphics and extra partitions"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by MollFlounders on 2011-02-12
Hi, 
I've had Ubuntu before, but still am basically a total beginner. I just brought a new laptop this morning and am trying to put Ubuntu 10.10 on with a partition for Windows 7. The installation went through fine, but when I restarted I was in the command line rather than having a graphic interface. 
 
Having looked through similar threads I've tried a few things, but not solved it yet. Some of the suggestions in other threads I couldn't understand how to do properly, so apologies if I'm repeating a previous thread. That's why I've come over to beginners talk!  
 
I have tried startx. This gave me a blank screen without even a flashing cursor. 
 
I tried ctl+alt+F7. This also gave me a blank screen.
 
I tried booting through "recovery mode" and it told me there is a problem with the graphics card. I didn't know how to solve it with the options it gave me, or how to copy and paste the information about the problem it was giving me. This is as far as I've got so far. 
 
My laptop is a Toshiba Satelite L655-S5155 with a 64 bit operating system 
Graphics Card Intel GMA HD, driver version: 8.15.10.2189
 
And to make it a little more complicated, I thought I'd just installed it wrong so tried again, and now have too many partitions because I think I just installed another set of ubuntu partitions on top of what I had just made :S I have no idea how to reconfigure them all now to get rid of the extra one I just created...
 
Any help would be very much appreciated!! thanks!

---

### Post by Hedgehog1 on 2011-02-12
Ahhh yes...  The old 're-install' and fill the disk with partitions.

Take comfort that you are not the first person to do this.  Nor will you be the last...

So, First things First:

When you reboot, are you getting an option to arrow down and boot into windows 7?  If so, do you get Windows 7 when you choose it?

If you can still reboot into windows 7, this fix will take one route.  If Windows 7 is hosed too, then it will take a second route.

Please don't go deleting extra partitions quite yet - We need to fix up your MBR (Master Boot Record) first.

---

### Post by MollFlounders on 2011-02-12
Hi! Thanks for replying! 
 
Yes, I get several options - about 3 for windows, and two for each of the linux partitions - and can still boot up windows 7 (its what I'm writing from now).

---

### Post by nm_geo on 2011-02-12
> **MollFlounders said:**
> Hi! Thanks for replying! 
 
Yes, I get several options - about 3 for windows, and two for each of the linux partitions - and can still boot up windows 7 (its what I'm writing from now).

What did you use to make the Ubuntu 10.10 install a CD or USB, and do you still have it?

---

### Post by Hedgehog1 on 2011-02-12
> **MollFlounders said:**
> Hi! Thanks for replying! 
 
Yes, I get several options - about 3 for windows, and two for each of the linux partitions - and can still boot up windows 7 (its what I'm writing from now).

Excellent!  This will be a **little** easier then.

The menus you are seeing letting you choose an OS are from GRUB.  Right now, your computer is using that to boot both Windows 7 and Ubuntu (well, what there is of Ubuntu on your system).

So we first need to get your computer booting from the Microsoft method.  This means doing a FIXMBR command after booting up on a CD that supports it.

Do you have the rescue or restore CD that came with your laptop?  Since you got it today, you should :D .

Do a search on how to get do a FIXMBR.  You will know it worked when you reboot the laptop and the GRUB menu does not come up - instead you will go right into Windows 7.

Once that is working, we will remove the extra partitions. Please don't remove them before you can boot into Windows with the MBR - otherwise your Laptop will not boot at all (Grub is using one of the extra partitions to boot up).

Post again when you are ready for the next step (or stuck).

:KS

---

### Post by MollFlounders on 2011-02-12
hm, well this is a bit strange but it looks like I wasn't given a restore cd when I brought it this morning. Can we do it without it?
 
I installed ubuntu using a cd (well, a dvd actually. I didn't have a cd to hand)

---

### Post by Hedgehog1 on 2011-02-12
> **MollFlounders said:**
> hm, well this is a bit strange but it looks like I wasn't given a restore cd when I brought it this morning. Can we do it without it?
 
I installed ubuntu using a cd (well, a dvd actually. I didn't have a cd to hand)

I guess most new PCs are not issued with them.

Inside windows itself, there is an option to burn a restore/repair CD.  In fact, you may be seeing a reminder (in the area with the little flag) telling you to do so.

This is their way of saving a few cents, I guess.

So lets have you burn that now. You will need to dig around in the control panel a bit to find it. It will make a CD that also has the drivers for your laptop in case you do ever have to reinstall windows.

There are also places to download 'repair' cd .iso files - but each version of windows uses a slightly different MBR.  So I am cautious of that for you, not being aware of your windows OS skill level.

---

### Post by Hedgehog1 on 2011-02-12
Oh - if the only media you have on-hand are DVDs, that is fine for burning the disk.

---

### Post by Hedgehog1 on 2011-02-12
> **nm_geo said:**
> What did you use to make the Ubuntu 10.10 install a CD or USB, and do you still have it?

nm_geo - does the 10.10 CD have a way to do a FIXMBR from it?  Or were you going another route?

I was planning to restore the laptop to pre-10.10 load condition, then have the OP run the liveCD and test for Ubuntu compatibility before reloading 10.10.

If you have an alternate solution, please speak up. :D

---

### Post by MollFlounders on 2011-02-12
ok I have a restore cd, which windows instructed me to label "Repair disk for Windows 7 64-bit". I'm just googling fixmbr, and will follow these instructions: [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)
 
I'm assuming this will work for windows 7 in pretty much the same way as xp.

---

### Post by Hedgehog1 on 2011-02-12
> **MollFlounders said:**
> ok I have a restore cd, which windows instructed me to label "Repair disk for Windows 7 64-bit". I'm just googling fixmbr, and will follow these instructions: [http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/](http://www.tech-recipes.com/rx/483/xp_repair_fix_master_boot_record_recovery_console/)
 
I'm assuming this will work for windows 7 in pretty much the same way as xp.

Well Done!

I see a great Ubuntian is hiding inside you, waiting to come out!

After you are rebooting directly into Windows, then we will remove all the partitions on the 'right' side of the windows/ntfs partition and give back that space to Windows.

:popcorn:

---

### Post by Hedgehog1 on 2011-02-12
MollFlounders,

The next major step is:

Backup windows from your laptop as it is right now.  This will give you a complete restore point for anything that might happen in the future.

I don't expect it will take more than 2 Data-DVDs

Store these with your repair CD/DVD - now you are 'safe'.

---

### Post by MollFlounders on 2011-02-12
phew! ok, I did that and it is now booting directly into windows. thanks for the encouragment!! 
 
By back up the laptop as it is now, do you mean something different than the systems restore cd I already made? I don't have any files saved in this computer yet.

---

### Post by Hedgehog1 on 2011-02-12
In this case, since you have no install CDs for the OS, I was thinking of a complete backup so you can put Windows 7 back to the 'factory default' level.

You don't have to do this - but I have a moral obligation to suggest it.

---

### Post by MollFlounders on 2011-02-12
ok that makes sense. I'm just trying to work out how to do it on windows with the options on offer.
 
I'm guessing its what they are referring to as a "system image", as this is described as "a system image is a copy of the drives required for Windows to run. ... it can be used to restore your computer if your hard drive ever stop working". 
 
Ok I will make a copy of that now!

---

### Post by Hedgehog1 on 2011-02-12
Thanks for backing up your system.

It sets a good example for others, too.

Moving on:

This FIXMBR step is 1/2 of how we remove a second OS on a dual boot with windows as the first OS.

The second step is to remove the unwanted partitions and give that space back to windows.

You have a choice of tools for this.  The Ubuntu boot CD offers gparted - which is more powerful than the Windows option of Disk Administrator.

However - the Windows tool is adequate (as of Windows 7) to do what we need done.  If you were doing this from XP, we would have to use gparted.

Disk Administrator is part of the system administration options in control panel.

I am sorry I am not more specific - I am doing this from memory (I am running off a USB stick with Ubuntu and I cannot boot into windows 7 myself until all the updates finish!)

You will see 1 or 2 little partitions on the left of the big NTFS/Windows partition.  Leave those alone. One contains the Windows 7 boot stuff - and if you have two the other little one  has the laptops manufacturer goodies in it.

Instead, one at a time start deleting the little partitions starting at the one furthest to the right.

Once they are all gone, you can click on the Windows/NTFS partition and tell it to expand to use the space.

Once this is done - you have un-installed Ubuntu and are back to the way your computer looked before your Ubuntu installation.

Then we can get to the original issue - getting Ubuntu loaded onto your laptop.

:KS

---

### Post by MollFlounders on 2011-02-13
ok I think I found where to do that. I'll just wait for the back up dvds to finish and then go ahead and get rid of those partitions. 
 
No worries, about the specificity: I'm working it out and learning a lot about how this all works at the same time :) Your instructions are very clear - I really do appreciate your help very much!!

---

### Post by Hedgehog1 on 2011-02-13
[SIZE="2"]I have two secondary motives in being so clear:[/SIZE]

(1) Others reading this later can do the same thing.

(2) Once you understand it, you can walk the next person though it!

\\:D/

But honestly - you are a quick study and *well worth the time!*

:KS

---

### Post by Hedgehog1 on 2011-02-13
Let me know when you are ready for the next step (or if you get stuck).

*You are now armed with the knowledge to install and un-install Ubuntu as much as you want to.*

Cool, huh?

---

### Post by MollFlounders on 2011-02-13
Ok I have 7 different partitions. I am thinking I keep these two, which are the first two on the left:
 
1.46 GB Healthy (Active, Recovery)
46.91 GB Healthy (Boot, Page File, Crash Dump, Primary Partition)
 
And delete these ones, which from left to right are:
 
181.91 GB Healthy (Primary Partition)
7.73 GB Healthy (Primary Partition)
207.23 GB Healthy (Primary Partition)
8.80 GB Healthy (Primary Partition)
11.72 GB Healthy (Primary Partition)
 
(I'm nervous about deleting the wrong thing!!)

---

### Post by Hedgehog1 on 2011-02-13
> **MollFlounders said:**
> Ok I have 7 different partitions. I am thinking I keep these two, which are the first two on the left:
 
1.46 GB Healthy (Active, Recovery)
46.91 GB Healthy (Boot, Page File, Crash Dump, Primary Partition)
 
And delete these ones, which from left to right are:
 
181.91 GB Healthy (Primary Partition)
[COLOR="DarkRed"][U]7.73 GB Healthy (Primary Partition)
207.23 GB Healthy (Primary Partition)
8.80 GB Healthy (Primary Partition)
11.72 GB Healthy (Primary Partition)[/U][/COLOR]
 
(I'm nervous about deleting the wrong thing!!)


The last four can be removed for sure.

Just to make sure that you are running Windows 7 off the 46gig partition, please bring up windows explorer and find out the size of the 'C:' drive.  If it is about 46 gigs, then you can also delete the 181.9 gig partition.

---

### Post by Hedgehog1 on 2011-02-13
Once all these partitions are deleted, you can expand the 46 gig partition to use all the space of the hard drive.

Normally I would ask you to do a defrag before an Ubuntu install,  but I have reason to believe the area at the 'end' of your disk is clear :D

When you boot the Ubuntu CD (umm, DVD for you), run it in liveCD mode and make sure that your video, sound and network connections all work.

This is a best test that you will be OK installing it.

Since this went wrong last time, we need to be careful.

Did you do a direct download or a bit-torrent of the Ubuntu ISO file?

I want to be sure you don't have a corrupted ISO.  Bit torrent checks for corruption, direct download does not.

Downloading it again (if you did a direct download) and burning a fresh CD (Ummm - DVD for you) is not a bad 'just to be safe' measure.

---

### Post by MollFlounders on 2011-02-13
Ok, so I managed to delete the other partitions using windows disk manager, and all is well. The C: drive was 46 gigs, so I now have only the 1.46GB, and one 464 GB partition with everything else on it. The backup of windows 7 took a while, but that worked fine too. 
 
I downloaded the original Ubuntu CD direct from the Ubuntu website. To be safe, I'm downloading it again now, but this might take some time. I've downloaded InfraRecorder to use that to burn the dvd this time, rather than the windows 7 dvd creator that comes as default.

---

### Post by JacquesPotter on 2011-02-13
How did you start this thread????  I can't find the option above....  PLEASE HELP...

---

### Post by Hedgehog1 on 2011-02-13
You have done very, very well.

You did not break down into tears (that I saw), stayed calm and collected and worked your way through this like a pro.

I give you a hearty [SIZE="5"]Well Done![/SIZE]  ):P

In fact - I hear-by name you an honorary hedgehog.  No greater honor can I bestow... 

:KS

Did you want to rest and try installing Ubuntu tomorrow?

Otherwise I be back in about 10 minutes...

---

### Post by MollFlounders on 2011-02-13
Hi Jacques, 
go back to the beginners forum page here: [http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)
and near the top on the left hand side is a grey button called "New Thread". Its in the same place as the grey "New Reply" button on this page. 
good luck!

---

### Post by MollFlounders on 2011-02-13
hehe, well I am very honored indeed to be an honourary hedgehog!! :)  I'm only going through it this easily because I have such good instructions :)
 
The ubuntu download is going to take a while and its pretty late on this end, so I think I will take a break and return in the morning, if that's ok with you. No tears this end so far! but plenty of yawns, and I don't want to make a silly mistake because I'm too tired. 
 
thank you so much for all your help so far Hedgehog! You're a star

---

### Post by Hedgehog1 on 2011-02-13
> **MollFlounders said:**
> 
The ubuntu download is going to take a while and its pretty late on this end, so I think I will take a break and return in the morning, if that's ok with you. No tears this end so far! but plenty of yawns, and I don't want to make a silly mistake because I'm too tired. 


Sounds very reasonable.  If I am not online when you try it again - you are now fully qualified to 'undo' an install if it goes wrong.

I think you are on solid ground now.

[SIZE="3"]*Happy Ubuntu(ing)*[/SIZE]

---

### Post by MollFlounders on 2011-02-13
Hi again! 

Well, its not been going too well over here. But I think I have a better understanding of why I had the problems in the first place. 

I've been trying to create a new Ubuntu cd by downloading the files via Internet Explorer. It took so long over night it timed out, then this morning the same thing happened (ie it timed out) after trying to download it for several hours. I think the problem may have been in my new windows 7/internet explorer, as it was also very reluctant to let me download and install Open Office. I finally managed to download and install firefox about half an hour ago, and through firefox successfully downloaded the Ubuntu files in minutes. Wish I'd done that from the start! 

But. Having burned my new Ubuntu files onto a dvd using infrarecorder, at a low burn speed as recommended, I tried to install Ubuntu from that disk and wasn't successful. Here's what happened:

- hit F12 when prompted, and selected to boot from CD
- I got the purple Ubuntu screen that just has two small logos at the bottom (a rectangle and a little stick figure in a circle) for a few seconds.
- I got the purple screen with Ubuntu and a row of dots for a few seconds...
- then the screen went black with a flashing cursor, followed by the following message:

Busybox v1.15.3. (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) mount:mounting/dev/loop0 on //filesystem.squashfs failed: Input/output error
Cannot mount /dev/loop0 (/cdrom/casper/filsystem.squashfs) on //filesystem.squashfs

any suggestions on what I'm doing wrong and how to fix it?
many thanks!

---

### Post by Hedgehog1 on 2011-02-13
MollFlounders,

Welcome back!

I am going to suggest you begin a new thread just about getting Ubuntu installed on your laptop.  We now need a separate set of skills to get Ubuntu installed (and a clean Ubuntu 10.10 CD/DVD to boot from).

Might I impose upon you to: (1) Change the title of this thread to something like 'How do I recover from multiple Ubuntu installs?' and mark it as solved.  This way, others who need to 'put their PC back to the way it was' can use this thread to do it.

Then will we work on loading Ubuntu on your new thread.

Thanks Honorary Hedgehog!

:popcorn:

---

### Post by MollFlounders on 2011-02-13
ok, will do that. Thanks!

---

