---
title: "Problems dual booting XP and Ubuntu"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by dneril on 2008-12-13
I would appreciate any help I could get on this.  I'm sure what I'm experiencing is a relatively simple problem, but since I'm a complete noob I'm having a lot of difficulty.

Recently formatted my hard drive, dividing it roughly in half, in two large partitions, one for XP, one for Ubuntu.  Installed XP first, then Ubuntu.  I've been working off of APCmag.com's "Definitive guide to dual-booting XP and Linux".

At this point I'm working off of Ubuntu, because I cannot load XP.  Tried modifying my menu.lst file so that I can load XP from my GRUB, but I continue to get "Error 11: Unrecognized device string"

I added the following text to the bottom of my menu.lst file:

title		Windows XP
root	        hd(0,5)
makeactive
chainloader +1

Tried rootnoverify instead of root, and a variety of different locations for XP.  I checked through, and it seems that I have partitions located at hd(0,2) hd(0,4) hd(0,5) and hd(0,6).  I eliminated (0,6) since this is Ubuntu running, and I have substituted each of the other three partition locations in the menu.lst.

I have also checked my device.map file - though I don't know if that is relevant.  It reads:

(hd0)	/dev/sda

Could anyone lend me a hand?  BTW I am running version 8.10 - thank you.

---

### Post by perixx on 2008-12-13
> **dneril said:**
> At this point I'm working off of Ubuntu, because I cannot load XP.  Tried modifying my menu.lst file so that I can load XP from my GRUB, but I continue to get "Error 11: Unrecognized device string"

I added the following text to the bottom of my menu.lst file:

title		Windows XP
root	        hd(0,5)
makeactive
chainloader +1

Hi dneril,

check out the probably best and most complete resource site on the web about booting, for your specific Grub-error, see this link:

```
http://users.bigpond.net.au/hermanzone/p15.htm#11
```

The MBR-section and the Grub-section (most notably the 'Grub Error' section) will help you a lot. 

By the way, I find it confusing that your Grub's menu entry for XP shows '(hd0,5)', which actually points to the 6th partition on your HDD. I presume, that you're only having one drive in your system here. XP must be on the first partition (hd0,0), so you need to replace your entry with the respective value.

EDIT: please note, that your system's referring to partition 1 as 'hda1' NOT 'hda0' (for PATA drives) or 'sda1' (for SATA drives). Grub uses (hd0,0), where the first number being the drive number, and the second number being the partition's number, starting from 0.

If you want to have an overview of all your partitions, run 'gksudo gparted' from the terminal; if it's not yet installed, do so by using the Synaptic paket manager (search for 'gparted'). You can view and modify all of your partitions graphically, to suit your needs easily with it. Be warned, though, that you can seriously blow up your data, if you don't know what your're doing! Viewing only, for info-purposes, is save, though.

greetz,

perixx

---

### Post by caljohnsmith on 2008-12-13
How about downloading the attached "boot_info.sh.txt" script, opening a terminal (Applications > Accessories > Terminal), and please post the output of:
```

sudo sh ~/Desktop/boot_info6.sh.txt
```
That will create a "BootInfo.txt" file on your desktop; please attach that to your next post so we can get a better picture of your setup.

---

### Post by perixx on 2008-12-13
**Additional info:** backup of MBR and bootsector prior to Ubuntu setup


I like to save the MBR and 1st bootsector (XP) after a fresh installation - in case something goes wrong with the Grub bootloader while installing Ubuntu; you can do this with the 'dd'-command, via an Ubuntu live-CD-session in a terminal:

```
sudo dd if=/dev/sda of=/media/USBSTICK/sda_bak.mbr bs=512 count=1
sudo dd if=/dev/sda1 of=/media/USBSTICK/sda1_bak.sec bs=512 count=1
```
- The first command copies your HDD's MBR (presuming SATA=sda) to the file 'sda_bak.mbr' on an USBSTICK (or whatever is appropriate for you). 'if=' means Input File, 'of=' Output File'. Of course, the MBR is no file, but the very first sector (512 bytes) on your HDD. 

- The second command copies your HDD's first bootsector (every partition has its own bootsector, XP's on the first partition) to '/media/USBSTICK/sda1_bak.sec' (or whatever you prefer). You can alter this command and save any bootsector you like, btw. 

Also, you might want to repeat those steps and make a second backup, after successfully setting up your dual-booting system.


If, for some reason, anything goes wrong when installing Ubuntu, you can recover just the other way round:

```
sudo dd if=/media/USBSTICK/sda_bak.mbr of=/dev/sda bs=440 count=1
sudo dd if=/media/USBSTICK/sda1_bak.sec of=/dev/sda1 bs=512 count=1
```
After that, you should have successfully recovered your MBR and XP's bootsector to the state of previous to installing Ubuntu, being able to boot XP without problems. Ubuntu won't be bootable anymore, though, you need to manually re-install Grub to access it again. 

**IMPORTANT:** it's vital to use 'bs=440' in the recovery string, to avoid writing an outdated partition table to the disk, after changes to the partitions have been made - which would result in a serious damage to the partition system.

NOTE, that the partition containing the bootsector you want to recover mustn't be mounted, but your source must be (e.g. /media/data on an NTFS partition). When using the live-CD, it might be neccessesary to mount/unmount it by hand in a terminal, e.g.:
```
sudo umount /dev/sda1
sudo mkdir /media/data
sudo mount -t ntfs-3g /dev/sda7 /media/data
```This unmounts XP's partition, so 'dd' can write-access it, and makes the folder '/media/data' to which you can mount the imaginary logical data partition in NTFS-format, which holds your bootsector's backup file.

You could, however, use some bootsector tools on the 'Ultimate Boot CD' to do basically the same job, if you prefer.


P.S.: interesting script, caljohnsmith!


perixx

---

### Post by logos34 on 2008-12-13
> **dneril said:**
> 
title		Windows XP
root	        [COLOR="Red"]hd(0,5)[/COLOR]
makeactive
chainloader +1



maybe it's just the typo (left parenthesis).  Should read:

> root (hd0,5)

---

### Post by caljohnsmith on 2008-12-13
> **perixx said:**
> 
If, for some reason, anything goes wrong when installing Ubuntu, you can recover just the other way round:

```
sudo dd if=/media/USBSTICK/sda_bak.mbr of=/dev/sda bs=[COLOR="Red"]512[/COLOR] count=1
sudo dd if=/media/USBSTICK/sda1_bak.sec of=/dev/sda1 bs=512 count=1
```

P.S.: interesting script, caljohnsmith!


perixx
About the script, forum member meierfra is the one who wrote it and deserves full credit for it. :) By the way, I just wanted to mention that restoring the MBR as you do above can be dangerous as you have it written, because the MBR contains both the boot code and the HDD's partition table. If you save the MBR prior to using Ubuntu to do repartitioning, and then restore the MBR as you do above, you will also restore the original partition table in the MBR. That can be a big problem if you used Ubuntu to make any partition changes, especially if you used Ubuntu to shrink the Windows partition. Also, the MBR partition table does not include the partition info about each logical partition, which is in the EBRs (Extended Boot Records) that are located 63 sectors before each logical partition. So bottom line, you could unfortunately really corrupt your HDD's partition table if you restore the original partition table that you had before making partition changes. 

If you just want to reinstall the Windows boot code to the MBR, you could instead do:
```
sudo dd if=/media/USBSTICK/sda_bak.mbr of=/dev/sda bs=[COLOR="Red"]440[/COLOR] count=1
```
But since installing a Windows MBR is easy to do from the Live CD, I don't think it's really necessary to make a backup of the original MBR. One easy way to install a Windows equivalent MBR is simply:
```
sudo lilo -M  /dev/sda mbr
```
But anyway, either way will work. :)

---

### Post by perixx on 2008-12-13
> So bottom line, you could unfortunately really corrupt your HDD's partition table if you restore the original partition table that you had before making partition changes.

If you just want to reinstall the Windows boot code to the MBR, you could instead do:
Code:

sudo dd if=/media/USBSTICK/sda_bak.mbr of=/dev/sda bs=440 count=1

You're right, caljohnsmith, I discussed this problem some time ago with 'mr. hermanzone' himself on the forum; it's maybe not really a good way to do it as I described - I'm changing my previous post to prevent troubles ahead :)
This should spare a resized XP partition- and/or changes to the partition table.
I haven't heard of your mbr trick so far, sounds nice to me! 
Anyway, either of our way beats using the bartPE disk, which takes twice the time to boot, than the Ubuntu live CD, I feel. 
That is, if nothing serious has happened.  

> maybe it's just the typo (left parenthesis)
Logos34, you must be correct about the typo - it matches exactly to the error description info on hermanzone's... still, I wonder, if he hasn't got multiple Windows systems installed, why does his boot entry point to an (obviously) logical partition? A standalone XP can't be installed there by default, and moving it to another partition is a tedious procedure, I suppose.


perixx

---

### Post by dneril on 2008-12-13
Thanks perixx, for referring me to that hermanzone page.  I'll be referencing it throughout this process.  I installed and ran the gparted application.  My linux-swap drive is at /dev/sda6; Ubuntu is at /dev/sda7 and XP (ntfs) is at /dev/sda5

So, I infer that XP should boot from (hd0,4)

Logos, you were right that I had incorrect syntax, in this regard.  Now that I've changed the text, I'm getting error #12 instead of #11.  Progress! :)

My text in the menu.lst file now reads as:

title		Windows XP
root		(hd0,4)
makeactive
chainloader +1

I looked into the hermanzone page and it suggests that I comment out "makeactive" in order to bypass error #12.  When I tried booting XP after doing that, I got the message "Starting up..." and, well, it didn't do anything.

It sounds like XP needs to be on the primary partition in order to function.  Since it is located on (hd0,4), will I have to reinstall it so that it might load?  Also, since gparted locates my files at /dev/sda5, should the root text read (sd0,4) instead?  I tried doing this and got error #23.

---

### Post by caljohnsmith on 2008-12-13
You are trying to boot XP from a logical partition, which is possible, but it takes some effort to get it to work. If you can post the output of that script from my previous post #3, it will give me the info I need to help you boot XP from a logical partition.

---

### Post by Moop on 2008-12-13
XP doesn't need to be on a primary partition and the correct syntax is hd0,4 and not sd0,4. 

Have you tried using (hd0,0) and (hd0,1) etc? I would try them all.

What's on the first 3 partitions?

---

### Post by dneril on 2008-12-13
Hi Caljohn,

I saved that file onto my desktop and ran the command as you described.  The output is as follows:
dneril@dneril-laptop:~$ sudo sh ~/Desktop/boot_info6.sh.txt
[sudo] password for dneril: 
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

Moop - There is nothing on the other partitions.  The reason that my system is set up in this way is because I formatted over previous installations. (e.g. vista - which is impossibly slow)

---

### Post by Moop on 2008-12-13
I would suggest starting over. Use a live cd or a XP cd and delete all your partitions. Then create the space you want for XP using the XP cd and install XP. Then install Ubuntu on the unused space. 

Save anything you need to external media before you delete your partitions.

---

### Post by dneril on 2008-12-14
Thanks for all of your help everyone.  I have opted to reformat my hard drive and reinstall both XP and Ubuntu.  Now things are working perfectly.  Again, thanks for your help.

---

### Post by caljohnsmith on 2008-12-14
Glad to hear you have it working.

---

