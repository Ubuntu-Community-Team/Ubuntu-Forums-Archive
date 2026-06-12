---
title: "out of memory??"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by carvish on 2010-12-11
I am dual booting win7 and Ubuntu. after dL 5 movies I get a "out of memory warning" I have a dedicated 160 gig hd for Ubuntu and when I look at my hard drives on win 7 , it shows only about 15 or 20 gig used, is this the norm?

 Knowledge is a dangerous thing!

Carvish

---

### Post by carvish on 2010-12-11
btw, im afraid to sign out because it took me about four hours to resign up for this forum talk thing, come on guys, it's only questions!!!!

---

### Post by AngusH on 2010-12-11
What were you getting stuck on in the sign up process?

Memory is not hard drive space (that's often called storage). Memory is RAM, which is where data is stored in the short term while programs are working on it. Did the message actually say out of memory or something slightly different (this is important :))

Regards
Angus

---

### Post by Hippytaff on 2010-12-11
How much RAM do you have?

---

### Post by carvish on 2010-12-11
I have 8 gig DDR3 Ram, 64 gig SSD for Windows 7, 160 gig HD for Ubuntu and 2-1 TB HD storage drives. Used wubi installer via- [http://www.youtube.com/watch?v=UdI8_92QTkQ](http://www.youtube.com/watch?v=UdI8_92QTkQ) , everything works well except this little glitch. I've even had my windows 7 crash (big surprise) and did a clean install with no effect to my Ubuntu.
carvish

---

### Post by nm_geo on 2010-12-11
Open terminal type 
```
free
```
Enter  Post

---

### Post by 3rdalbum on 2010-12-11
If you installed using Wubi, then you only have 15GiB (or whatever you chose when you installed, but 15 is the maximum) space for Ubuntu. If you are going to keep Ubuntu, I would recommend removing Wubi and installing Ubuntu using the Ubuntu-based installer on the CD. This way you will have more room to move.

---

### Post by carvish on 2010-12-11
I did have Ubuntu installed straight up on the drive with grub 2 as the boot-loader, but I kept getting the famous "grub puts not found" message. Have they fixed that issue? I tried to fix the issue via YouTube, but to no avail The issue signing in was my fault, using up my 5 chances a couple of times, etc. etc.

---

### Post by carvish on 2010-12-11
............total       used       free     shared    buffers     cached
Mem:       8196460    2732416    5464044          0      30736    1832760
-/+ buffers/cache:     868920    7327540

---

### Post by carvish on 2010-12-12
ok, Ive downloaded the newest version 10.10 I have made a stick drive out of the iso, should I uninstall the Wubi version and proceed to install the new version? What happens if the grub2 acts up again and I can't load either OSes? Why is it that Ubuntu is so user friendly, but in order to use grub 2 you need a 18 page user manual?

so many questions, so little time!!!
carvish

---

### Post by Hippytaff on 2010-12-12
You can remove Wubi before you install 10.10. but going to add/remove programmes in the windows control panel. If grub plays up with the 10.10 install we can cross that bridge if we come to it.

---

### Post by carvish on 2010-12-12
well this is odd, ubuntu or wubi isn't there to remove??

---

### Post by mikechant on 2010-12-13
Don't know about your 'missing' wubi install, but as far as grub2 is concerned, if you've had problems with it you might do well to install without a boot loader (Installer option for this is under 'manual partitioning' I think) and then manually install 'legacy grub' afterwards (boot from the LiveCD in 'try Ubuntu' mode to install legacy grub, you won't have boot option for the installed Ubuntu at this stage). 

It may be old and have less features but I find it rock solid, and there's generally no compelling reason for most people to use grub2 (there probably will be when the BRTFS file system becomes the default, since legacy grub doesn't support it, but that's a year or two off).

I'm in a rush at the moment and don't have time to look but I'm sure there's plenty of info about installing legacy grub on these forums.

Another important tip: Assuming windows currently occupies the whole disk, use Windows' own disk management facilities to shrink the main Windows partition *before* you start the install. Don't use gparted or the Ubuntu installer to shrink the Windows partition, this could make windows unbootable.

---

### Post by oldos2er on 2010-12-13
Reading through this thread, it's not at all clear to me whether the 'memory' referred to in the title is RAM or hard disk space. Can you download the boot info script, run it, and post the RESULTS.txt here? Instructions: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by carvish on 2010-12-14
unless terminal sucks a lot of ram out of the system,

---

### Post by walt.smith1960 on 2010-12-15
I bought this shareware program before I discovered Linux--I had several Windows installs for various purposes.  You do have to pay for it or put up with 1 minute delays but once i mastered its nuances it works pretty well.

[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

I use it for partitioning then use the Ubuntu installer to format.  You can have something like 128 primary partitions and I'm using ext4 with no problems.  The big thing for me is to make sure GRUB is installed in the relevant partition, not in the MBR.  Installing GRUB in the MBR is supposed to be recoverable but it ain't easy.

---

### Post by carvish on 2010-12-29
Well I did it , and against all logic.I found a copy of "Linux Format" at the book store with a copy of Ubuntu 10.10 on disk and ready to go. So I installed over the entire disk, 160g. Now that damn grub2 doesn't show my windows 7 in the menu on boot. Any ideas? Don't forget, I'm a Noob

---

### Post by carvish on 2010-12-29
> **oldos2er said:**
> Reading through this thread, it's not at all clear to me whether the 'memory' referred to in the title is RAM or hard disk space. Can you download the boot info script, run it, and post the RESULTS.txt here? Instructions: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)


8g of ram and about 2.224Tb ROM

---

### Post by carvish on 2010-12-29
> **oldos2er said:**
> Reading through this thread, it's not at all clear to me whether the 'memory' referred to in the title is RAM or hard disk space. Can you download the boot info script, run it, and post the RESULTS.txt here? Instructions: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)



 "No such file or directory" and thats a copy and paste

---

