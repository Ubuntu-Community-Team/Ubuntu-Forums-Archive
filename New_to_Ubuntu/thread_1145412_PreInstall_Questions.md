---
title: "PreInstall Questions"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by cynserino on 2009-05-01
Hi everyone! From the title, I guess my questions would be best placed here. I'm not exactly a freshman to computers, but I haven't really tried Linux yet. Now that I work from home and storage is cheap, I've decided to give it a go. So here are my questions:

32-bit or 64-bit? Is there a real difference with Linux?

And next is more of a hardware set-up question. I have three HDDs that I plan to use.  2 IDE (1 300GB, 1 20GB) and one SATA 1TB. Everything will be formatted prior to the install to prevent problems. Are there any issues when setting this up as follows...

20GB = Linux only ext3/swap
300GB = Windows only ntfs
1TB = Media/Non Install Win Programs ntfs*(with windows pagefile)

And any recommended MediaPortal like programs?

Thanks for the help guys!

EDIT: Are with 1GB RAM, what should I allocate to the swap?

---

### Post by supersonicdarky on 2009-05-01
- get x64 if cpu supports it
- there's xbmc, linuxmce, etc (google "linux media center")
- 20G might not be enough if you install enough programs
- you should make a swap partition (1G max I guess)

---

### Post by Niniel on 2009-05-01
20 GB ought to be enough even if you install a number of programs. The typical installation of 9.04 is 4 - 5 GB, and that's with all the standard software. Subtract 1 - 2 GB for the swap partition, and you'll still have more than 10 GB of free space.

---

### Post by Roadbloc on 2009-05-01
If you have a 64 bit machine, ubuntu will not let you install the 32 bit version on. at all.

---

### Post by Paqman on 2009-05-01
> **supersonicdarky said:**
> 
20G might not be enough if you install enough programs


You'd be fine with normal Linux apps. The only huge fat installs that might threaten to use up the whole drive would be VMs or large Windows apps (eg: games) installed through Wine. Both of the latter live in your /home directory and can take up a lot of space.

---

### Post by Paqman on 2009-05-01
> **Roadbloc said:**
> If you have a 64 bit machine, ubuntu will not let you install the 32 bit version on. at all.

Yes it will. It's the other way around that you can't do.

---

### Post by Roadbloc on 2009-05-01
oh, yeah. :oops:
My mistake...

---

### Post by cynserino on 2009-05-01
> **Paqman said:**
> You'd be fine with normal Linux apps. The only huge fat installs that might threaten to use up the whole drive would be VMs or large Windows apps (eg: games) installed through Wine. Both of the latter live in your /home directory and can take up a lot of space.

I won't be using either of them. I'm going to dual-boot with Windows XP but that will have it's own HDD (300GB) because I know the games get out of control size-wise. Also most of the save data like documents and projects will be stored on the TB separate from both OSes.

Are there any tips to setting up the partitions on the Linux drive?

---

### Post by supersonicdarky on 2009-05-01
you may possibly want a separate /home

---

### Post by nandemonai on 2009-05-01
> **cynserino said:**
> I won't be using either of them. I'm going to dual-boot with Windows XP but that will have it's own HDD (300GB) because I know the games get out of control size-wise. Also most of the save data like documents and projects will be stored on the TB separate from both OSes.

Are there any tips to setting up the partitions on the Linux drive?

Separate /home/ partition is always handy. ;)

---

### Post by Paqman on 2009-05-01
> **supersonicdarky said:**
> you may possibly want a separate /home

+1 to this.

The reason it's good is that your user account including all your preferences and application settings are stored there. Having it on a separate partition means you can reinstall the whole OS without messing up your settings.

---

### Post by Jimmynemo2 on 2009-05-01
If you do the seperate /home, how do you point ubuntu to use that one instead of the default? Also, since programs are in that same folder, does that mean you wouldnt need to reinstall programs if you had to reinstall ubuntu?

---

### Post by fugaki on 2009-05-01
> **Roadbloc said:**
> If you have a 64 bit machine, ubuntu will not let you install the 32 bit version on. at all.

This is not true.
I am running a dual boot on my laptop, 64 bit Windows, and 32 bit Jaunty.

---

### Post by Paqman on 2009-05-01
> **Jimmynemo2 said:**
> If you do the seperate /home, how do you point ubuntu to use that one instead of the default? 


During partitioning you can assign parts of the filesystem to mount on different partitions. Linux uses a file called fstab (file system table) to keep track of what is mounted where. It sounds complicated, but it's actually pretty simple, and extremely flexible.

> 
Also, since programs are in that same folder, does that mean you wouldnt need to reinstall programs if you had to reinstall ubuntu?

The actual executables aren't in the folder, just their user settings. For example, your browser bookmarks and plugins would be in there. So you would have to reinstall the apps, but as soon as you installed them they would be exactly how you had them set up last time.

It's not just apps either, all the OS settings like wallpaper, preferred applications, etc are all kept there.

---

### Post by doas777 on 2009-05-01
[here]("https://help.ubuntu.com/community/HowtoPartition") is a great guide to partitioning, with images and what not. your scheme looks good, but I strongly advocate the separate home partition, perhaps on a 100GB chunk of the TB drive. 

it looks like your asking the right questions. if it works with your hardware, you'll have a wonderful experience with ubuntu.

good luck,
Franklin

---

### Post by cynserino on 2009-05-03
Thanks for all the answers guys. After all the reading I've been doing, the separate /home/ is something I'll do. I have another few questions as I'm waiting for the 1TB to come in. Using GParted for the partitioning, how should it all look before anything is installed? And what about adding another IDE drive for the install? A 10GB for the actual install and a 20GB for the /home/. I only have a single DVD-RW so I have one more IDE channel open and a spare 10GB laying around. So after all this is installed, physically it will look like this:

IDE1: 300GB/20GB
IDE2: DVD-RW/10GB
SATA: 1TB

Too much? I'm honestly trying to keep to one partition per HDD just from past bad experiences. The smaller HDD's will probably be replaced in a few months with bigger ones and that will be a whole new set of questions then.

---

### Post by Paqman on 2009-05-03
> **cynserino said:**
> 
Too much? I'm honestly trying to keep to one partition per HDD just from past bad experiences.

Not a bad idea at all. Having your /home and / on separate drives actually avoids a slight performance hit that you'd get by having them on separate partitions on a single drive. Basically the heads would be slapping back and forth on a single drive.

---

### Post by presence1960 on 2009-05-03
> **Roadbloc said:**
> If you have a 64 bit machine, ubuntu will not let you install the 32 bit version on. at all.

Not true. When I first started using Ubuntu I installed the 32bit version because I read the posts of all the naysayers of 64bit. They were saying it was a pain, not supported etc, etc. Then I discovered the x86-64 users section of the forum and read in there. Next thing I know I was downloading the .iso for 64bit. Burned it to a CD and did a clean install.

64bit capable CPUs will run 32 bit OS's.

---

### Post by Paddy Landau on 2009-05-03
> **cynserino said:**
> Are with 1GB RAM, what should I allocate to the swap?
> **supersonicdarky said:**
> you should make a swap partition (1G max I guess)
The recommended size for the swap is double your RAM. So, if you have a 1Gb RAM, then make your swap 2Gb. I've read that the extra space is needed when you hibernate.

---

### Post by Keithhed on 2009-05-03
bump

---

### Post by Paqman on 2009-05-03
> **Paddy Landau said:**
> The recommended size for the swap is double your RAM. So, if you have a 1Gb RAM, then make your swap 2Gb. I've read that the extra space is needed when you hibernate.

Nope. To hibernate your swap only needs to be the same size as your RAM, because hibernation just copies the whole contents of RAM straight into swap.

I usually recommend swap = RAM for hibernation, otherwise swap = 1GB.

---

### Post by cynserino on 2009-05-04
> **Paqman said:**
> Not a bad idea at all. Having your /home and / on separate drives actually avoids a slight performance hit that you'd get by having them on separate partitions on a single drive. Basically the heads would be slapping back and forth on a single drive.

> **Paqman said:**
> Nope. To hibernate your swap only needs to be the same size as your RAM, because hibernation just copies the whole contents of RAM straight into swap.

I usually recommend swap = RAM for hibernation, otherwise swap = 1GB.

> **supersonicdarky said:**
> - get x64 if cpu supports it
- there's xbmc, linuxmce, etc (google "linux media center")
- 20G might not be enough if you install enough programs
- you should make a swap partition (1G max I guess)

Ok, I'm going to sum up what I've read so far. 

[LIST]
[*]1 partition per HDD is a good idea.
[*]At least 1GB for swap.
[*]Use 64-bit if my hardware supports it.
[/LIST]
So the HDD's will look like this:

[LIST=1]
[*]300GB - Windows XP Pro (ntfs)
[*]10GB - Ubuntu 64-bit (ext3) / swap?
[*]20GB - /home (ext3) / swap?
[*]1TB - Extras (music, movies, tv, projects)
[/LIST]
Which hard drive would be better for the swap partition, the install drive or the home drive? And for the 1TB, which filesystem is recommended if both Windows and Ubuntu will be accessing it (i.e. playing music/movies, storing unfinished websites and graphics)?

---

### Post by Paddy Landau on 2009-05-04
> **cynserino said:**
> Which hard drive would be better for the swap partition
I would say put the partition on the 300Gb drive. As you are likely to access the Windows drive very little while booted on Ubuntu, there will be virtually no access clashes.

> **cynserino said:**
> And for the 1TB, which filesystem is recommended if both Windows and Ubuntu will be accessing it (i.e. playing music/movies, storing unfinished websites and graphics)?
That's a contentious one. If the 1Tb is a removable drive and you intend to pass it between different computers, you'd probably want to go for maximum portability: NTFS.

If you intend to use it mostly from Windows, then also NTFS, for efficiency.

If you intend to use it mostly from Ubuntu without needing the maximum portability, then I'd suggest ext3 for efficiency (that's what I do).

Alternatively, you could partition it into two; NTFS on one partition and ext3 on the other.

To access ext3 from Windows, I suggest either of the following two programs. They will allow you to access your Ubuntu partition and, if you format it as ext3, your 1Tb drive. Both of them have a "read-only" option if you do not wish to write to the ext3 partitions.

[LIST=1]
[*][Ext2 File System Driver for Windows]("https://sourceforge.net/project/showfiles.php?group_id=43775"). Despite its name, it accesses ext3 perfectly fine. Try this one first.
[*]If that doesn't work for you, use [Ext2 IFS for Windows]("http://www.fs-driver.org/"). It only accesses ext2; in other words, it *will* access ext3 but without regard to the journalling.
[/LIST]

---

### Post by cynserino on 2009-05-09
Thanks for the help guys. I got everything installed and running finally. I thought I'd share my story considering what happened.

Hardware installed with no problem. That's the easiest part if you ask me. So I start up, install Windows. Nothing wrong so far. Go to restart Windows just to get that out of the way. Went smooth, then an HDD image just in case. Next was the Ubuntu install. Actually went well. I though I'd get stuck somewhere, but no problem. It was a little slow, but what do you expect from a LiveCD? 

So the GRUB got installed and I thought 'great, I should be done.' Nope, no go. Nothing at all. SYSTEM DISK ERROR. I needed to change my BIOS. Apparently it decided that the 1TB (storage) should be the boot drive. So had to fix that.Restart and it jumps into Windows. Huh? Restarted it and again Windows...

So I pop the LiveCD back in and go solution hunting, thinking maybe some one had fixed this before. Found one, tried it. Now an Error 13 when trying to get into Windows... So more hunting and then I just figured time to get my hands dirty. Every solution I found didn't work. Changing the mapping in the GRUB, some #magic code, nothing worked. 

So on a whim, I opened up the drive map for GRUB and switch the two OS drives in the map. Restart and guess what? It worked. Has anyone had to do this before? I couldn't find anything about editing that file, just the menu.lst. Anyway, I'm off to a fun start with Ubuntu. Wish me luck!

---

### Post by Paddy Landau on 2009-05-09
Your error was most curious. I'm pleased you got that fixed, and thanks for sharing.

Good luck, have fun, and come visit often to ask questions and answer others!

---

### Post by thomasr on 2009-05-09
wrong thread

---

