---
title: "dual boot- want to remove ubuntu"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by amsunshine0917 on 2009-05-24
Okay, I have my desktop computer set up to dual boot Vista and Ubuntu 9.04. I had Vista first, and when I installed Ubuntu I let it set up the partitions automatically to run "side-by-side" Well, that ended up somehow not leaving enough memory for ubuntu and now I can't install any updates or drivers for Ubuntu and I just want to take it off my computer completely. I have read all over the internet, and I have found two ways:
 
1. Run compmgmt.msc Well, when Ubuntu partitioned my hard drive it didn't label them. They are all blank "Primary Partition"s and I don't know which is what.
 
2. Use the Vista Installation Disk. This seems like the easier option but A-I don't know how (lol, I know it should seem easy I just don't wanna mess anything up) and B- I don't know if it would delete my personal files (pictures, etc) and I don't have enough removable storage to back it all up :/
 
Any help would be greatly appreciated :)

---

### Post by Bölvaður on 2009-05-24
Wise words of wisdom :

Have 20GiB / partition for Ubuntu
Always manually do the partitions your self.

---

### Post by cwsnyder on 2009-05-24
Do you still have an Ubuntu Live CD?  System >> Administration >> Partition Editor should show you your Ubuntu partitions, what they are used for, and allow you to a) Remove the Ubuntu partitions and b) Restore the Windows partition to its full size.

This is less likely to restore your Windows Vista installation than anything available for free from the Windows side.

---

### Post by CaptainMark on 2009-05-24
Using windows boot disks will delete your personal files, youll need to back them up. Why don't you try burning an Ubuntu live cd and using the partition editor to erase the Ubuntu partition and expand the Windows partition.
Heres the link for making the disc [https://help.ubuntu.com/community/GettingUbuntu#Download%20the%20Live%20Desktop%20CD]("https://help.ubuntu.com/community/GettingUbuntu#Download%20the%20Live%20Desktop%20CD")
Boot from the CD and once loaded go to System>Adminiistration>Partition Editor
The rest is easy to do, just locate the ubuntu partition and delete it

---

### Post by CaptainMark on 2009-05-24
Also i forgot to add if you choose to do this is probaly better to use ubuntu 8.04 ive found the live disc to be more stable than 9.04

---

### Post by welshboy on 2009-05-24
What you can do is in Vista, go into My Computer, and right click on the computer and choose Manage (I think)  Then click on Disk Management, it should then show you that one partition is formatted to NTFS and the other is an unknown partition.

You can delete the linux partition from there by right clicking on it, and choose Delete Partition, but please for the love of all that's holy, make sure you back up everything on your linux AND your windows drives in case it goes wrong.

You can also shrink the drive in Vista too, you right click on the drive and select Shrink Volume.

But please, I can't emphasise this enough, PLEASE!!  If you're not sure about it, then don't do it.

Welshboy :)

---

### Post by CaptainMark on 2009-05-24
The only problem I see with this is that Windows as I remember it (up to XP SP3) wont let you expand another partition after youve erased or edited the Ubuntu partition, without downloading additional software, which reminds me that gParted is also made free for windows (I think).  Download this and you should be able to play with the partitions to your hearts desire.
Again you have to back up anything you dont want to lose just incase, i have an old iPod which i reformatted as a standalone fat32 drive for keeping important stuff on anytime i intend on mesing with system files.

---

### Post by CBHedricks on 2009-05-24
Hey - there is also the bootloader to worry about as well.  If Vista is handling the bootloader all will be fine and dandy if you delete the Linux partition.  If GRUB or other bootloader is inplace you may need to boot from the Vista disk and use the repair console to fix the boot loader process.

BACKUP YOUR DATA... even if you have to get an external drive... Doing anything with your hard disk can equal disastor for numerous reasons.

If you end up having to re-install vista you will loose everything that is on the computer so a back up is critical if you have important data.

CB

---

### Post by yanceypd on 2009-05-24
Please chec the forums before trying to remove ubuntu or resizing the partitions.  Grub is installed now and without doing the right procedure Vista will have a boot error after the removal. One of the regular people here will point the way.  Backup while you can still boot.  I use dual boot to separate disks to play.

---

### Post by presence1960 on 2009-05-24
after deleting the Ubuntu partition(s)- you were told a couple ways to do that above, if Vista bootloader is not in control when you boot your machine- you will need the Vista DVD and follow this to restore Vista bootloader: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

