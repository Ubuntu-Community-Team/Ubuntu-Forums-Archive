---
title: "Two physical HDD, two OS, and three storage HDD."
date: 2009-09-13
forum: New to Ubuntu
---

### Post by Kill-Switch on 2009-09-13
Hi, I'm still new to the linux world and wanted to ask about dual booting with two physical HDD. Since I have tons of HDD, I thought it would be better to set it up this way but I'm still not sure on this so I wrote up questions to avoid future problems.

1) Are there any disadvantages on separating the two OS on two physical HDD? I read it in the official ubuntu page that dual booting on one HDD has disadvantage such as when ubuntu gets installed after windows, ubuntu would get slower due to the write speed on the slower side. Is there any problem with seperating with this method?

2) I have to keep windows on my first HDD and linux on the second HDD correct? I heard windows must be on the first HDD since it'll overwrite the first HDD if linux was there.

3) I have three additonal internal HDD and want to make these as storage (music, video, etc.). When I'm on windows, I could see all the storage HDD but what happens when I install linux on the second HDD? The setup looks would look like this on my computer:

[First HDD] Windows OS
[Second HDD] Linux OS
[Third HDD] Storage 1
[Fourth HDD] Storage 2
]Fifth HDD] Storage 3

Could Linux access all my storage HDD as well? I know my windows can but I'm not sure if it'll work with Linux. They are all internal HDD.

4) I searched this forum and found out how I install two OS with two HDD but I just want to re-check it since the thread was old. First, I need to unplug the first HDD (windows OS) then connect my empty HDD to install linux. After I install it, I connect back all the HDD so it'll look like the setup above and I'm finished. Is it this simple or am I missing something?

Thank you for reading.

---

### Post by rob-ward on 2009-09-14
You should have no problem installing ubuntu on the second drive, I am not sure why you have being told to take the first HDD out, I have never don that and I would have thought that because the hard drive names would change that it would cause probnlems with the grub config. Does anyone else knopw whay he should take the first windows HDD out???

You should have no problem accessing your othr storage drives from both OS's however you may have to be carefull how you use the hibernate feature as if you hibernate windows then load linux and change a file and then reboot windows the file changes can be lost so you need to be carefull of theat.

The other suggestion that I have is that if you have spare room on a different drive other than the one that you are installing ubuntu on it can be advantagous to create a swap partition on that drive instead of the Ubuntu OS drive, this should give slightly better performance. This is however optional and not needed to be done if you are not sure how to.

Hope that helps, still not sure about taking the first drive out though, hopefully someone else will have an idea why.

---

### Post by megamania on 2009-09-14
> **Kill-Switch said:**
> 4) I searched this forum and found out how I install two OS with two HDD but I just want to re-check it since the thread was old. First, I need to unplug the first HDD (windows OS) then connect my empty HDD to install linux. After I install it, I connect back all the HDD so it'll look like the setup above and I'm finished. Is it this simple or am I missing something?

From my experience:
- if you want a grub-selectable windows/ubuntu dual boot, you have to keep both drives plugged in when installing. The installer will write grub to the boot hard disk, and then will let you choose the OS at boot time.
- if you want to select the boot drive from bios, then YES, you have to take out the windows hard disk when installing on the other disk.

I haven't managed to get the Ubuntu installer to ignore the first disk and install Ubuntu on the second disk with no dual boot.

---

### Post by oldfred on 2009-09-14
1: The difference in write speeds is so small between the inner & outer sectors of a hard drive as to not noticeable. Once you get used to Ubuntu you can research some optimization that will have larger inpact, but that depends on your exact hardware configuration and what software you are using. This is for advanced users and I have only tried one or two things and my system runs great. I think is better to have operating sytems on different hard drives. The only advantage of making your Ubuntu drive first in the BIOS is that the MBR will be for ubuntu and the MBR for the windows drive will not be modified and could be reset to boot first and work as a windows onloy system. Ubuntu will configure the windows boot correctly if you do that. See next comment.

2: Windows likes to be the first hard drive as it was designed to be the only hard drive on a computer. I recently added a third drive to my computer and temporarily had a fourth old windows drive that I wanted to copy some data from. I installed a second Ubuntu on the third drive and it automatically configured the correct boot for my windows on the first drive and the old windows on the fourth drive. The only thing windows overwrites is the MBR - master boot record which is the first thing on a hard drive that the computer reads to point to the actual boot files. Even when windows overwrites the MBR it is relatively easy to reset it back to ubuntu/grub.

3: Linux will see all your drives/partitions in Nautitus - the file browser, but if you want to permanently mount them in a specific location you can edit a file. If you want this look for info on editing fstab & mounting.

4. I would not unplug a drive. Ubuntu will automatically configure all operating systems it finds on all hard drives. If one is unplugged it will not configure that one and you have to do some manual editing to find the windows entry.  Some have be scared that they may overwrite their windows if the wrong drive is selected when installing. Just be sure which drive you choose to install to and to be safe you (of course) have all important data backed up. 
Herman's site has a lot of examples of installing and is worth the read.
[http://members.iinet.net/~herman546/]("http://members.iinet.net/%7Eherman546/")

If your system has 1GB or more of memory swap is less important as it will rarely be used unless you do some very memory intensive activities.

You should never hibernate in a dual boot configuration unless you know you are coming back to the same system. Any writing from the other boot into the hibernated drive will potentially corrupt the drive.

---

### Post by Kill-Switch on 2009-09-14
Thank you very much for the helpful replies! I should've started posting here earlier, I was confused for a long time with this new operating system but all the problems that I was worried about is solved in one day. I was about to give up but posted here for last resort, which I regret not doing it much earlier.

I have never used the hibernation feature before so that isn't a issue. Thank you for reminding me about it, I might've tried it in the future but I now know it isn't wise to do that. 

> 4. I would not unplug a drive. Ubuntu will automatically configure all operating systems it finds on all hard drives. If one is unplugged it will not configure that one and you have to do some manual editing to find the windows entry. Some have be scared that they may overwrite their windows if the wrong drive is selected when installing. Just be sure which drive you choose to install to and to be safe you (of course) have all important data backed up.> Ubuntu will automatically configure all operating systems it finds on all hard drives.Is this just for ubuntu? I'm trying out ubuntu in the beginning but I wanted to try out other versions of linux as well in the future. For example, if I tried out another distro after getting used to ubuntu and linux, such as debian, arch, fedora, slackware, would they automatically configure all operating systems it finds on all hard drives as well?

English is my 2nd language so I apologise if I made any grammar and spelling mistakes or comprehended incorrectly. I want to recheck if I made any mistake with the new installation instruction:

1) Install windows to the first HDD
2) After I finish, install linux to the second HDD while the first HDD with windows is still connected.
3) After I finish, I just have to reboot to switch the operating system correct? I was thinking I had to install Grub but it seems like it'll create it for me after I install linux on the second HDD.

If this is correct, I never knew it was so simple. I thought it takes a lot more effort doing dual boot with two physical hard drives.

---

### Post by oldfred on 2009-09-14
Ubuntu will install Grub to the first boot drive. If that is the windows HD it will overwrite the windows boot in MBR. As long as you have your windows install CD you can alway run the fixboot to reinstall window boot if you ever want to go back to just windows.
Some of the other linux distributions do not always find all the other operating system. Learn about menu.lst and what the entries are. You can often copy entries from one system to another. Of course in a little over a month with 9.10 we may be converting to GRUB2 which is different.
If you are planning a lot of versions look at this site, it is older but still pretty current. He installs 145 systems on 2 harddrives. It helps to see what planning is involved and some of the issues different distrubutions have.
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by louieb on 2009-09-14
lol - think I'll throw my 2 cents worth in - based on dual booting several PC's over the last 3 years.

> First, I need to unplug the first HDD (windows OS) then connect my empty HDD to install linux.Did my 1st dual boot that way. Reasoning I can't screw up my windows install if the drive is un-hooked.  Now I use manual partitioning when installing - unless I have a brain-fart - the OS gets installed where I want. And just as important GRUB get installed where I want. 


> I heard windows must be on the first HDD All windows wants is to be installed in a primary partition with the boot flag turned on. 1st drive - 2nd drive - 2nd partition 2nd drive - whatever drive and partition, as long as its a primary partition and the boot flag is on.  

I like to have windows on the 2nd drive in the boot order. Just so I can keep its MBR pointing to the Widows boot loader.

> Since I have tons of HDD Its GRUB  you may have to configure manually. Things that confuse the GRUB installer are: a mix of pata and sata drives; and changes to the boot order of the drives. Don't know yet how GRUB2 has addressed this.

> 
[Third HDD] Storage 1
[Fourth HDD] Storage 2
[Fifth HDD] Storage 3
 Really like the way your keeping data separated from the OS(s). 
  
 Ubuntu will handle multiple drives just fine. Should not have any problems.

---

### Post by Kill-Switch on 2009-09-14
> **oldfred said:**
> Ubuntu will install Grub to the first boot drive. If that is the windows HD it will overwrite the windows boot in MBR. As long as you have your windows install CD you can alway run the fixboot to reinstall window boot if you ever want to go back to just windows.
Some of the other linux distributions do not always find all the other operating system. Learn about menu.lst and what the entries are. You can often copy entries from one system to another. Of course in a little over a month with 9.10 we may be converting to GRUB2 which is different.
If you are planning a lot of versions look at this site, it is older but still pretty current. He installs 145 systems on 2 harddrives. It helps to see what planning is involved and some of the issues different distrubutions have.
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Thank you for the link. My computer came pre-installed with windows. I have the recovery CD from the factory image so I think it'll be fine if I mess up. 

Also, in the future, I'm changing my HDD with the operating systems to SSD (solid state disks). The installation should be the same method as above correct?

And just one last question, I have a old computer with ubuntu installed. The graphic card is ATI radeon 4550 with 3GB ram. I have the proprietary drivers for ATI activated. Whenever I try to play videos on it, it's very slow. It plays fine when the screen is small but when I maximize the mplayer, the frame rate drops to around 1 fps. Is there any solution for this or is it better just to go back on windows to play the video? The videos are mp4, mkv, avi.

---

### Post by oldfred on 2009-09-14
I do not know about SSD's. I suggest some research on what type of formatting would be best, the nice thing about Linux is there are many not just FAT32 or NTFS. You may want to turn journaling off to prevent excessive writing of data, but that also has issues. You trade speed for security.

I read ATI has issues but I use Nvidia so I have not followed them closely. Video drivers seem to be one of last major issues and the video card mfg all think there system is so proprietary and Linux so small of a user base that they do not provide top notch drivers.

---

### Post by Cypher1101 on 2009-09-14
I have a hd 3870 with proprietary drivers enabled and I have some problems with my display during video playback too. Hopefully, you'll at least find a way to work around them, if not fix them entirely. The formats you're playing might run better with vlc, which has all of the codecs related to those formats built into it. 

I would, however, like to point out that .mkv files have been incredibly problematic for me regardless of what operating system I run them in. Since you still have access to windows, don't feel bad about booting into it so your videos playback correctly. I used to do it too before I found out about proprietary drivers, which fixed playback on my system.

I don't know anything about ssds, but other then that I think I have a pretty similar set up with my hdds. I only have two, but my ubuntu partitions are both on the slave drive, along with a storage partition used primarily by my windows install. On that note, have you considering partitioning your 2nd hdd so that it isn't all reserved for ubuntu? You could give some of it to an ntfs partition so that you could store videos for use by windows or linux. Most posts I've seen suggest that your root partition really only needs about 10 gigs. The rest can go to storage. Also if you do the partiitioning by hand it's easier to mount your windows drives. I also recommend installing grub to the hard drive that its on so that you never have to worry about repairing ntloader if you decide to revert back to windows only at any time. By doing these things I had no reason to unplug any hdds during install

---

### Post by Kill-Switch on 2009-09-15
Thank you for the replies again.

> **Cypher1101 said:**
> I have a hd 3870 with proprietary drivers enabled and I have some problems with my display during video playback too. Hopefully, you'll at least find a way to work around them, if not fix them entirely. The formats you're playing might run better with vlc, which has all of the codecs related to those formats built into it. 

I would, however, like to point out that .mkv files have been incredibly problematic for me regardless of what operating system I run them in. Since you still have access to windows, don't feel bad about booting into it so your videos playback correctly. I used to do it too before I found out about proprietary drivers, which fixed playback on my system.

It seems like there's people with ATI who can play the videos fine. I just did sudo apt-get install mplayer. I might be missing codecs or something else but I'll try to look more on that after I successfully install the dual-boot. I can't do it yet since my computer is sent to repair but I should get it back in 2 or 3 days. I'm currently on my old computer with ubuntu installed. Maybe I wouldn't have problem with it on my newer computer so I'll just have to wait and see.

> **Cypher1101 said:**
> I don't know anything about ssds, but other then that I think I have a pretty similar set up with my hdds. I only have two, but my ubuntu partitions are both on the slave drive, along with a storage partition used primarily by my windows install. On that note, have you considering partitioning your 2nd hdd so that it isn't all reserved for ubuntu? You could give some of it to an ntfs partition so that you could store videos for use by windows or linux. Most posts I've seen suggest that your root partition really only needs about 10 gigs. The rest can go to storage. Also if you do the partiitioning by hand it's easier to mount your windows drives. I also recommend installing grub to the hard drive that its on so that you never have to worry about repairing ntloader if you decide to revert back to windows only at any time. By doing these things I had no reason to unplug any hdds during install
Sorry if I made any mistakes since my knowledge in HDD/partition is limited but are you saying to do that so I could make more space for windows as well? For windows, the only reason why I want to keep it is because I'd like to play games that is incompatible with wine in the future. I haven't played games in a long time but I gave in at D3. I'd like to fix the video problem on linux as well so I wouldn't have to go back to windows.

---

### Post by Zero++ on 2009-09-15
It sounds like you have the OS hard drives under control. I would format your storage drives as a NTFS partition. Ubuntu plays well with NTFS and Windows uses it almost exclusively at this point. Just a thought.

---

### Post by Shujah on 2009-09-15
> 1) Are there any disadvantages on separating the two OS on two physical HDD?
No, it's better management actually. After all said and done its always better to have separate OS in their separate places.

> 2) I have to keep windows on my first HDD and Linux on the second HDD correct? I heard windows must be on the first HDD since it'll overwrite the first HDD if Linux was there
I'm not sure I get you, you'll decide where to install Ubuntu, MS is competitive but not crazy enough to wipe out an OS without your consent. If you Install Ubuntu after Windows, Windows gets automatically detected and included in Grub, i.e. you see Windows in Grub Boot Menu alongside Ubuntu. If Windows in Primary Master Grub is written in that HDs MBR if Ubuntu is Primary Grub goes there. So perhaps you should change the HD sequence make the Ubuntu HD primary master and Windows HD secondary before installation. This will install Grub on Ubuntu HD which will allow you to bypass grub completely (by changing boot priority via Bios) if you mess up, which if you are completely new to *nix won't be that unusual, secondly Vista and Win7 write at MBR by default and having Grub in Windows HD MBR can create problems at time of upgrade. I think you can also change Grub location by selecting advance options during installation and selecting the relevant HD (still google it to make sure).   

> 3) I have three additional internal HDD and want to make these as storage (music, video, etc.). When I'm on windows, I could see all the storage HDD but what happens when I install Linux on the second HDD?

You'll be able to access all the storage HDs and many more don't worry about that. Try NTFS as it is supported out of box and is more stable plus has no file size limitation like fat32 (4 Gb). Another thing to keep in mind is to consider making a separate /home partition. This will come in handy if you need to reinstall/ upgrade Ubuntu and also if you want to try new distros.

---

### Post by Kill-Switch on 2009-09-18
Thanks once again for the helpful replies.

My computer should arrive on the 21st so I can't wait to try it.

While I'm waiting, I was thinking of setting up dual-boot with this computer. This computer only has one hard drive so I'm going to dual boot by creating partition. I just have one question regarding this. If I dual boot windows vista and linux, I'll have to create a partition. My hard drive has 320 GB. Is it wise to give my linux at least half of it (160 GB)? I'll be on linux full time and only boot back into windows if I feel like playing games (which is only about 1 hour few times a week). Other than that, I'll be on linux and have my images, videos and everything else on this. 

I'm confused on the partition part. If I give linux 10 GB partition, that'll mean I only have 10GB of space for my root and all my spaces for images, videos, mp3, etc. correct? Since I want all those files on my linux, isn't it better to give linux a lot more GB or am I mistaken on something?

---

### Post by oldfred on 2009-09-18
You can make windows as small as it will let you plus 10 or 20GB for growth. You only need 10GB for linux as a minimal install. If you make /home an additional partition then root size is only important if you install lots and lots of applications. I also like a separate /data partition for most data so /home only has local config files in it. /data then needs to be as big as possible depending on how much data you have.

Use Vista's partitioner in disk management to resize its partition. Old problems seem to have been solved with gparted and others but it is still safer to use Vista to shrink its partition. Defrag, defrag again & resize. If problems, try disabling system restore, pagefile, (in advanced settings in computer properties) and hibernate option (in power management). Don’t forget to turn them on back later.
Starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can now  deal with it but should have the round to cylinder unchecked, so this is why to use Vista to resize its partition.

---

