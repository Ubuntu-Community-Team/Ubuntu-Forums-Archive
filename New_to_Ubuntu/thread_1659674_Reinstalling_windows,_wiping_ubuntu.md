---
title: "Reinstalling windows, wiping ubuntu"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by Larry_Underwood on 2011-01-04
Hi all,

I am a real newbie when it comes to do much more than simple things on my computer. I recently installed ubuntu and completely wiped windows off and i do not have a recovery disc.

I have tried getting a windows 7 iso and installing it but windows cant recognize my harddrive because of ubuntu. My only other option in the install is to upgrade which i can not do.

So my question is, what is the simplest way to reinstall windows? After i get windows back on i want to create a partition with ubuntu.

Thanks 

Dude

---

### Post by anystupidname1 on 2011-01-04
I suggest you:
1 boot from your ubuntu livecd/liveusb or [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
2 use gparted to create an ntfs partition
3 boot from w7 install dvd and install
4 if you're still interested in installing ubuntu dual boot after that see:
[http://wubi.sourceforge.net/](http://wubi.sourceforge.net/)

Note: You typically, can do the reformating with the W7 DVD but your post seems to indicate YOU cannot for some reason...

---

### Post by cgroza on 2011-01-04
> **anystupidname1 said:**
> 
4 if you're still interested in installing ubuntu dual boot after that see:
[http://wubi.sourceforge.net/](http://wubi.sourceforge.net/)

If you want to do a real dual boot, then format the whole drive as an NTFS and when installing Ubuntu, there is an option that will alocate some space for Ubuntu and install it there. I forgot the name of that option but it should be obvious.

---

### Post by ppv on 2011-01-04
You might first want to backup all your data using ubuntu.

A legit windows installation disc would be needed if you just want to install windows first. 

If you have it then you could just pop in the disc into the drive and reboot the computer. If the computer is not set to boot from the CD drive first then it needs to be set so in the bios. After the computer boots from the windows CD you could continue installing windows. At the point where you chose the partition, delete existing partitions and create new ones as required. This will wipe off all the partitions and the drive.

---

### Post by Bucky Ball on 2011-01-04
Boot from Ubuntu CD, choose 'Try without installing', System->Administration->Gparted partition Editor.

Kill all Ubuntu partitions. Install Windows on the free space, using only as much space as you need for your partitions and leave the rest free.

Once booted successfully into new Windows install, download 10.04 LTS (NOT 10.10 as there are issues at the moment, major), burn disk image and boot from that.

Install and when you get to the partitioning section choose manual partitioning. You will see your Windows partitions clearly in there (NTFS). Just avoid them. At least you are going to need these three partitions for Ubuntu:

/ = root, where the OS lives (probably no more than 15Gb)
/home = where your stuff lives (big as you like)
/swap = 2Gb max, at the end. 

You can add others but these are defaults in there. Except for /swap which will format itself, make the others EXT4.

Follow your nose. The Ubuntu install will pick up the fact Windows is present, re-write the MBR accordingly and create a menu list which includes all present OSs. Remove CD and reboot when asked and you should be flying. 

In a nutshell ... ;)

---

### Post by Larry_Underwood on 2011-01-05
Thanks a lot guys, worked great. i had to clear everything but i had already done that in the last week.

Cheers,

Dude

---

### Post by Bucky Ball on 2011-01-05
Great news! Please mark as solved from 'Thread Tools'. ;)

---

### Post by ekjsim on 2011-01-05
What kinda major issue is present with Maverick?

---

