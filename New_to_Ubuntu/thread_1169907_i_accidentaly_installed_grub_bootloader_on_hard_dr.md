---
title: "i accidentaly installed grub bootloader on hard drive"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by linux000019 on 2009-05-25
help, what do i do now?

alright, i dont have any type of linux on this computer at all, its not even my computer; i was installing ubuntu to a usb drive(which won't install btw, always freezes @ 15% and gives me a error during write message) and when doing so, forgot to double check the drive to install the bootloader too(its in advanced options) so now i screwed it up.

---

### Post by desm on 2009-05-25
Ok, I'm not sure I understand entirely what you're saying. So I shall say what I think you are saying and what you should do about it if you are saying that.

You have a pc which is running windows. But you've now accidentally installed GRUB to the hard disk and cannot get onto windows anymore (or just want to get rid of grub).

This is easy, 

   1. Insert the Windows XP CD into your CD drive and restart your computer. If you are prompted, select any options required to start (boot) from the CD.
   2. When the text-based part of Setup begins, follow the prompts. Select the repair or recover option by pressing R.
   3. If you have a dual-boot or multiboot system, select the installation that you want to access from the Recovery Console.
   4. When you are prompted, type the Administrator password.
   5. At the command prompt, type 'fixmbr' (without the qoutes) and this will write a new partition table.
   8. At any time, you can exit Windows Recovery Console by typing Exit at the command line.

When you have done this you will only be able to access your windows install, so if you have multiple windows installs, or others OS's on the HDD you will not be able to access them without installing a bootloader or returning to your previous windows config (if you were using windows as a bootloader).

That was taken from here: [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058) and edited.

---

### Post by linux000019 on 2009-05-25
very quick and helpful, except me being the unprepared newbie that i am, i haven't got a windows xp cd, just 2 usb drives and 2 computes, 1 of which will now not boot.

---

### Post by Didius Falco on 2009-05-25
> **linux000019 said:**
> very quick and helpful, except me being the unprepared newbie that i am, i haven't got a windows xp cd, just 2 usb drives and 2 computes, 1 of which will now not boot.

Use the one that still works to go here and get a boot disk:

[http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm)

Regards,

Didius

---

### Post by linux000019 on 2009-05-25
i looked around the site, lots of xp boot disks, none that looked helpful; i do not own a 3 1/4? 3 1/2? inch drive; i do own usb flash drives. can you help me?

---

### Post by linux000019 on 2009-05-25
IF I DO THIS IS THE PROBLEM GOING TO FIX OR WORSEN?
 
 
 
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)
 
 
 
 
 
Something happen to a windows Master Boot Record ([[COLOR=#e8a02c]MBR[/COLOR]]("http://en.wikipedia.org/wiki/Master_boot_record")) that you&#8217;re responsible for? Want a very quick, very easy way to restore it with nothing but your craft, native intelligence and a liveCD?
Be cautious here - you&#8217;re working with your disks in a very direct manner. If you don&#8217;t have everything backed up or are unsure of anything, you may want to wait until you have a standard Windows CD/DVD.
Boot into your Ubuntu LiveCD on the offending machine. Once Ubuntu starts up, go to *System -> Administration -> Software Sources* and enable (by checking it off) the *Universal* repository.
Now, open a terminal session (*Applications -> Accessories -> Terminal*) and type the following:
[INDENT]sudo apt-get install ms-sys
[/INDENT][[COLOR=#e8a02c]ms-sys[/COLOR]]("http://ms-sys.sourceforge.net/") is a program used to write Microsoft compatible boot records.
Now you&#8217;ll need to figure out what partition is the one hosting your Windows operating system. Back in the command line, type:
[INDENT]sudo fdisk -l
[/INDENT]That will list the available partitions. You&#8217;re looking for a partition that says something like
[INDENT]/dev/sda1 1 9327 74919096 83 NTFS
[/INDENT]The two important bits are the &#8216;*/dev/sda1*&#8216; which is the partition itself and the &#8216;*NTFS*&#8216; which tells us it&#8217;s a Windows formatted partition. So your Windows partition exists on your drive sda and it&#8217;s partition 1. The MBR for drive sda (assuming you boot into windows using it&#8217;s native boot loader) is what you want to repair.
We want to fix the MBR on */dev/sda*. To do so, type:
[INDENT]sudo ms-sys -m /dev/sda
[/INDENT]You&#8217;ll want to change the &#8217;sda&#8217; bit if your results from &#8216;*fdisk -l*&#8216; are different. If for instance your windows install is on *sdb* or *hda*.
Once you do that, reboot the machine, removing the LiveCD from the drive and Windows should come back to you.
Sure, you could do this by inserting the correct Windows CD and booting into repair mode from it - but I find the Ubuntu way a bit faster and I&#8217;m more likely to have an Ubuntu LiveCD on me than a Windows CD.

---

### Post by linux000019 on 2009-05-25
anyway, since im post so much; i keep this new post in my old post; it seems that when installing ubuntu from my crunchbang live cd; the manual operation where i specified file systems partitions and format WILL install; and the guided use all of disk selection freezes @ 15% then gives me a error pop up. thoughts?

---

### Post by Didius Falco on 2009-05-25
Super Grub Disk has a downloadable, bootable USB image:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

You can use it to get back into Windows. Be sure and read the documentation carefully.

That should at least let you get into windows until you can borrow an XP CD from a friend long enough to repair the MBR.

Regards,

Didius

PS - I've never used that "ms-sys" utility, so I really can't say about that - but, hey, you're in a bind, how much worse could it get?

What's the error message you are getting from the Ubuntu installer? What version are you trying to install?

---

### Post by powel212 on 2009-05-25
> IF I DO THIS IS THE PROBLEM GOING TO FIX OR WORSEN?

I have used ms-sys under exactly the same circumstances you mentioned above and it worked perfectly and easily too.

Follow the instructions [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/) 

and don't worry

Powel

---

### Post by linux000019 on 2009-05-25
> **Didius Falco said:**
> Super Grub Disk has a downloadable, bootable USB image:
[]("http://www.supergrubdisk.org/")What's the error message you are getting from the Ubuntu installer? What version are you trying to install?


it freezes @ 15 % detecting file system; before a input/output error saying ignore/retry/cancel pops up.

xubuntu 9.04

---

### Post by Didius Falco on 2009-05-26
> **linux000019 said:**
> it freezes @ 15 % detecting file system; before a input/output error saying ignore/retry/cancel pops up.

xubuntu 9.04

Hi, 

Did you get your Windows MBR fixed?

Here is a guide top the different boot options available for the Live CD. Read through it and pay close attention to the F4 and F6 options - it could be as simple as booting into Safe Graphics mode.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If none of those work for you, there is an Alternate Installer that should do the trick, which can be downloaded here:

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

Regards,

Didius

---

