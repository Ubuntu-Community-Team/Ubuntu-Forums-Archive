---
title: "clean install of win 7"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by DarinB on 2009-11-01
I have a vista box i added jaunty to...... so i use the grub boot loader. will i be able to do a clean install or upgrade of the vista portion to win 7? or will i lose my grub and not be able to boot into Ubuntu???? Any way how to do this?

---

### Post by LewRockwell on 2009-11-01
upgrading might preserve your current partitioning and MBR contents but don't bet on it

make sure you've done your back-ups and clones so that you can restore the exact clone if you experience a catastrophic failure

we use Clonezilla

seriously, if your time is of value to you...you'll become familiar and versed with back-ups, clones, and long-term data storage options BEFORE you make changes to your current properly-running operating system(s)

windows is a beast, it does not play well with others, and many computers with pre-installed windows come with OEM disks that...when used...reset the ENTIRE hard drive...thereby smashing and trashing EVERYTHING else on your machine

as always, your mileage may vary, buyer beware, and buyer be ware

.

---

### Post by Gadgetech on 2009-11-01
Windows will overwrite your master boot record (MBR) and break grub, but you can fix it afterwards. You will need to be able to boot to an Ubuntu Live CD in order to make the repair. 

Check out this thread [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113).

I've also done a writeup on my blog that summarizes the info from the thread, [[COLOR="Blue"]Windows 7 Hosed My Boot Record[/COLOR]]("http://tuxtweaks.com/2009/01/windows-7-hosed-my-boot-record/").

**Be very careful** during the Windows installation to make sure you only let it format the Windows partition.

---

### Post by DarinB on 2009-11-01
>  Re: HOWTO: Restore GRUB (if your MBR is messed up)
Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

looking up at above link using a live cd with terminal how do find out what my / or /boot hdd number is??? i know my / is /dev/sda5 my /home is dev/sdb1 my /mnt/music is dev/sdc1 so what would that be for grub hd(something)?? and is it the root that i need or the /boot partition?? not sure i understand the way to do this

---

### Post by LewRockwell on 2009-11-01
some dirt on the grubsters


here are the links:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


drs305 is GREAT!

kudos!

.

---

### Post by DarinB on 2009-11-01
Hmmm! since i have a separate /home and /mnt/music, wouldn't it be easier to do a full install of windows 7 then if i can't get the grub back do a clean install of Ubuntu. but now where near as fulfilling as getting it to work by fixing the grub.

---

### Post by DarinB on 2009-11-01
omg (grub2) a new grub on top of this, do you guys want my head to explode!!!!! 
I don't understand grub 1 yet!!!! Ahhhhh!

---

### Post by LewRockwell on 2009-11-01
> **DarinB said:**
> omg (grub2) a new grub on top of this, do you guys want my head to explode!!!!! 
I don't understand grub 1 yet!!!! Ahhhhh!

let the fun continue unabated...lol!

.

---

### Post by DarinB on 2009-11-01
> Re: HOWTO: Restore GRUB (if your MBR is messed up)
Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot. 
Back to my question anybody?
looking up at above link using a live cd with terminal how do find out what my / or /boot hdd number is??? i know my / is /dev/sda5 my /home is dev/sdb1 my /mnt/music is dev/sdc1 so what would that be for grub hd(something)?? and is it the root that i need or the /boot partition?? not sure i understand the way to do this

---

### Post by QLee on 2009-11-01
[QUOTE=DarinB]Back to my question anybody?[/QUOTE]

Well, we are supposed to stay focused on your question, that's the purpose of this forum.

[QUOTE=DarinB]looking up at above link using a live cd with terminal how do find out what my / or /boot hdd number is??? i know my / is /dev/sda5 my /home is dev/sdb1 my /mnt/music is dev/sdc1 so what would that be for grub hd(something)?? and is it the root that i need or the /boot partition?? not sure i understand the way to do this[/QUOTE]

If you did not make a separate /boot partition (and you probably didn't, then your /boot will be where you think it is. As long as there aren't any partitions that you haven't told us about on which you installed a GNU/Linux system.

Can we assume that you haven't upgraded to GRUB2 yet?

Then hd0,4 is sda5

In a terminal, enter the command mount, that is one way to see what is mounted, where.

---

### Post by ken0069 on 2009-11-01
Hey guys & gals, you'll have to forgive me as I'm kinda new to this Linux stuff, sort of, but all this grub stuff, etc is confusing?  What I've done is setup an extra drive for each operating system, ie, this Asus P5Q motherboard has 6 SATA ports and right now I got 4 different operating systems on 4 different drives in that one box.  I can pick the OS that I want to boot in BIOS and if one of'em horks up then I haven't lost anything on any of the others.  Right now that box has Suse 11.1, XP, Vista and 7 and I'm looking to add ubuntu that I downloaded last night to that mix shortly via a 5th drive.  
 
So is this just a case of "I can do this therefore I will regardless of how much trouble it is" type thingies or am I missing something here?:mrgreen:

---

### Post by QLee on 2009-11-01
[quote=ken0069]
So is this just a case of "I can do this therefore I will regardless of how much trouble it is" type thingies or am I missing something here?:mrgreen:[/quote]

You're missing something but that is OK because you are new. GNU/Linux is about choice. You have the ability to boot the way you do because your system can be setup that way, not everyone has the same choices. In addition, some would think your method is more complex than just choosing from a menu, different people find different methods to be more or less complicated due to hardware limitations and/or skill level. Another addition, not everyone can afford to go out and buy a new HDD for each OS they want to try, even at today's rates and not everyone is capable of opening a case and adding and/or they are using a laptop. More drives consume more power and some people are trying to use the least power possible for a useable system. I've touched on a few points, if you think longer and more carefully about it, you can probably think of a few more. 

But remember this thread is supposed to be about the OPs question.

---

### Post by DarinB on 2009-11-01
entering the mount command did not show a boot partition but i did think i had a swap on but it did not show up. there for to understand the sda4 is hd0,4 would the sdb1 then be hd1,0? and the sdc1 be hd2,0?just trying to understand the numbering???

---

### Post by DarinB on 2009-11-01
sorry i meant sda5 is hd0,4 etc

---

### Post by QLee on 2009-11-01
> **DarinB said:**
> sorry i meant sda5 is hd0,4 etc

Yep! You seem to be understanding correctly. 

You didn't see a /boot partition when you issued the mount command because you don't have a separate partition for /boot.
The /boot I mentioned previously is the "/boot" in your "/", the bottom line is that your "boot" partition is the partition that has the /boot on it that the MBR points to (it could be separate or like yours, a folder on /). The /boot folder is where GRUB finds the menu (for simplicity I won't be more complete with the explanation).

Edit: I just noticed your point about swap, yes, the mount command should have shown you mounted swap.
You could look in the file at /etc/fstab, it's the filesystem table for static mounts that the system does at boot time and it should show what you are using as swap.

---

