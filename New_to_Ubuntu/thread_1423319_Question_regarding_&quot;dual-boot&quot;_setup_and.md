---
title: "Question regarding &quot;dual-boot&quot; setup and hard drives"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by GameOverDood on 2010-03-06
Hi :),

I'm interested in a dual-boot setup for my home computer but I'm not sure if I should have Ubuntu and Windows on two separate hard drives or on the same one? 

I currently have a single 500GB hard drive but I'm willing to invest on an additional hard drive if you guys suggest it. Also, I'm going to use Ubuntu for web browsing, document processing, and every-day stuff (listening to music, watching movies, etc.). Windows is going to be mainly for games and Windows-specific applications like Adobe products.

**Edit**: I guess the real reason why I'm trying to decide between the two is because I need to know which is the most safest and reliable way of having a dual-boot setup? I don't mind troubleshooting issues but with time constraints I can't always be spending too much time on a problem. In other words, should an issue arise, I'd like to know which setup would be the quickest to resolve.

---

### Post by kayvortex on 2010-03-06
You can install Ubuntu and Windows on the same hard drive just fine, but they will need to be on different *partitions*. This is the only real technical step involved in installing any OS, actually, not just Ubuntu.

There's lots of info on partitions and partitioning your HDD here and on the internets in general, and we'll be happy to help if you have any questions. I'd suggest that you read up on it (or ask) before you do anything if you don't already know about it, since (like I said before) it's the only really technical thing that you will do.

In terms of safety/reliability/ease, there's no meaningful difference between installing on the same disk or on separate disks, it's just that partitioning a disk that already has an OS on it is more work than partitioning a fresh new one because you will likely have to make room for the new partition. Think of it like adding a new room to a house: at the end of the day a room is a room, but making space for it involves a bit more work than buying the house next door! (Edit: analogy only works if you live in terraced housing.)

Then again, it's not too much work (unless your disk is full, in which case you need a new HDD anyway!).

---

### Post by Kixtosh on 2010-03-06
Setting it up on one hard drive is not an issue at all in my experience. In fact, during the installation process, there is a partition management procedure which will automatically resize and create partitions as necessary. This is totally painless IMO. You can also manually adjust the settings, but that might be somewhat daunting for first time users (at least, it was to me, and it took me a few tries to figure out the exact consequences of my decisions when using the manual settings). 
 
As for which is best, I'm not sure what issues might be a concern when using a single drive, and what issues might be a concern when setting up a dual hard drive system boot.
 
Ubuntu will install the GRUB (*GNU GRand Unified Bootloader)* boot loader package. Once finished, this means that when your computer first starts up, the GRUB menu will appear after the BIOS splash screen that you might normally see. Ubuntu will be selected by default, and will start on its own after ten seconds, if you don't intervene, but you will also have the option to scroll down to a "memtest" option and your Windows O.S. also.
 
*Edit: I forgot to mention that you should probably defragment your Windows partitions before installation about three times over. Sometimes they don't like being resized if they are fragmented.*

---

### Post by GameOverDood on 2010-03-06
Thanks for the replies! I think for now I will test it with just a single hard drive and see how it goes. (I guess it'll save me some money for the time being as well.) I understand there will be a learning curve involved so I'm mentally prepared for what's to come lol. 

One other question I had is that I read an old article a while back that Ubuntu can't modify Windows files, and vice versa, unless the files are stored on a partition with FAT32 as the file system. Is this still true even to this day?

@ **Kixtosh**: Thanks for the heads up about the defragmentation. I'm planning on reformatting my computer completely anyway so I think I'll be good. :)

---

### Post by Kixtosh on 2010-03-06
> **GameOverDood said:**
> ... One other question I had is that I read an old article a while back that Ubuntu can't modify Windows files, and vice versa, unless the files are stored on a partition with FAT32 as the file system. Is this still true even to this day? ...No, that is no longer true for Linux (and hasn't been for a while), which is why some people are able to use Linux LiveCD's to rescue files from damaged Windows hard drives. I don't think Windows will be able to identify your Linux files however. Of course, if you intend to actually open something like a Word document, created in Windows, with Open Office, using Ubuntu ... I'm not sure if that works.
 
If you're wiping everything clean, then you should have a happy experience IMO (I did, at least, and everything was 95% operational, including ancient Netgear wireless "b" cards, without any tweaking).

---

### Post by RevKeltina on 2010-03-06
> **Kixtosh said:**
>  Of course, if you intend to actually open something like a Word document, created in Windows, with Open Office, using Ubuntu ... I'm not sure if that works.
 

I do this all the time with files I bring home from the office.  They are Windows, I am not.  I can use open office to open Word documents and Excel Spreadsheets without a problem.  I can also save them with the proper Windows extensions and take them back to the office the next day!

---

### Post by GameOverDood on 2010-03-06
Thanks for the responses. I think I'm ready to roll over onto Ubuntu soon. I already have the distro CD burned for installation. Right now, I'm just waiting for my files to finish backing up. 

Wish me luck! :D

---

### Post by cap10Ibraim on 2010-03-06
> **GameOverDood said:**
> One other question I had is that I read an old article a while back that Ubuntu can't modify Windows files, and vice versa, unless the files are stored on a partition with FAT32 as the file system. Is this still true even to this day?

When I'm using Ubuntu I work within windows 7 documents folder 
to keep the two OS synced no problem at all

---

### Post by kayvortex on 2010-03-06
Yeah, I'll second that: if you're going to wipe and install, then the only problem you'll likely have is deciding how big to make your partitions (and maybe if you want separate partitions for /boot etc. -- I wouldn't bother).

My advice would be this: put the liveCD in first, boot off the CD and wipe the whole disk and make your partitions now using gparted (ask if anything is too technical). You should make your first partition for Windows (too much hassle if you don't), and all the following ones for Ubuntu. Then, install Windows first and Ubuntu last, and then just tell the OS which partition to install in when you get to that step since you've already made the partitions.

Another tip would be doing an Ubuntu Install before anything else so that you're familiar with the steps involved and then just cancelling the thing at the end: nothing gets installed, and you'll be prepared on what to do when you do the install proper.

---

### Post by cacycleworks on 2010-03-06
Another option ... I do this for friends who are tired of windows but aren't quite ready to fully wipe it from their drives.

[LIST=1]
[*]Defrag Windows partition from within windows
[*]Boot to a live CD (i personally like knoppix 5.1)
[*]Run GParted to shrink the windows partition to about 20G more than it currently uses
[*]Reboot to Ubuntu install disk (I use the ALT cd because it's faster -- but is command line, so no mousey)
[*]i add partition for /home of at least 100G*
[*]I add partiton for / of the remainder minus the amount of RAM I have
[*]The final partition is for linux-swap. If swap is larger than RAM, you can suspend or hibernate pretty reliably.
[*]Be happy.
[/LIST]

A little bit of google can teach you LOTS about this process. :-)

PS: *-I do a separate /home because when you want to upgrade to next ubuntu (10.4), you reformat / but leave /home alone. This minimizes the custom settings you have in your programs. Firefox won't lose history, etc. You will lose apt-get installed programs, however, so those will need to be reinstalled. I personally like this method of upgrading to new distribution.

---

### Post by Kixtosh on 2010-03-06
To be honest, I actually find backing up the hardest part of the whole process, as a novice. Once everything is backed up correctly, it doesn't bother me to install things this way, and then that, two or three times over, until I figure out exactly what is going on.
 
On my last installs, I was using W2K for dual boot, so:
 
**1)** I wiped the drives clean with the W2K process, leaving blank space on the hard drive beyond what I thought I would ever need in Windoze (I formatted the entire drive first, removing all partitions, then created just the two partitions I wanted for the Windoze O.S. and NTFS file partition.).
 
**2)** I used the LiveCD of Ubuntu to install, including the instruction to use the largest amount of free space, or some similar language. This is still semi-automatic, once selected, and works pretty much like cruise control really (but still not quite as easy for a novice as fully automatic partitioning without any custom user options).
 
Otherwise, if you do want to mess with partitions yourself, the advice above from cacycleworks seems pretty solid, now that I've gone through some of those processes myself once or twice (or have at least heard of them).
 
Just in case you don't know, Knoppix, which was mentioned by cacycleworks is a Linux distribution that is intended to work only from CD (and RAM), without ever being installed (it's the first experience I ever had with Linux, in 2005). Another option is Puppy Linux, which also works entirely from a CD, and is very light and fast, as well as being extremely novice friendly. Either way, you get to use Gparted to modify partitions however you want, if you prefer to do that instead of letting the installation process do this automatically for you.
 
Here are some useful links, if your not afraid of reading a bit. It can be confusing at times, and you might end up with that "options paralysis" "oh my head hurts" feeling. That's certainly the effect it had on me.
 
Best of luck! Just remember: if your stuff is already adequately backed up, then you've got nothing to loose, except a few hours of your time.
 
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by GameOverDood on 2010-03-06
W00t! I'm back. The Ubuntu installation went smoothly. I did have to download and install some extra stuff, like some media codecs and a few applications, but for now everything seems to be running like it should.

Thanks for the tips everyone, and also Kixtosh I actually had found that guide that you posted earlier: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) ...and ended up following that for dual boot installation. The method I used was to install Windows first and then Linux. 

Again, thanks everyone for the help. :)

---

### Post by Kixtosh on 2010-03-07
Good for you ... well done! I told you that backing up your sh!t was going to be the hard part!
 
Windows first, Linux second seems to be the consensus (it's also what I did).

---

