---
title: "Removing windows?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by Toke on 2009-11-30
I have gotten to the point in my dual boot laptop where I have not booted windows for months and could use that extra space for better things.

My plan so far is to boot with a live cd, start the partition editor and simply delete the windows partition and drag the linux one to take up the space.

My hope is that this will free up a lot space without disturbing my excellent Ubuntu 9.04 installation.

My worry is that there will be some problem on booting as the "other operating system" is now missing.

Does anyone know?

---

### Post by mbzn on 2009-11-30
You need not worry about that, simply boot into Ubuntu, go System>Administration>Partition Manager remove the partition(Windows) then just remove the lines containing this partition from grub(depending on version ie. Grub/Grub2) not sure how to do this. You can then add a partition or resize your linux partition over this space(Please note that it is HIGHLY recommended to do a proper backup of all partitions being edited). 

Hope this helps and that someone will soon tell you what files to edit.

---

### Post by Toke on 2009-11-30
I have no idea how to edit grub, and to resize my partition I am pretty sure I have to unmount it first, that is, boot from a cd or pendrive.

---

### Post by QIII on 2009-11-30
To modify your Linux partitions, you will need to use the LiveCD since the partition cannot be mounted.  You are correct there.

Here is a bit of info regarding changes to menu.lst:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by candtalan on 2009-11-30
The easiest approach is to - whatever actions you end up doing - leave the partitons as named the way they are currently. 

This does not prevent you changing the size of partitions, larger or smaller, and so on, but it would suggest that you do not delete a partition at least. By, for example, deleting the *contents* of the Windows partition, maybe by simply formatting it, then the partition name remains the same and there is no need to edit any files such as grub.

The most simple action would be to leave the old Windows partiton, formatted as convenient (might be to remain as NTFS maybe), and make use of this as a data partition in future.

More elegant solutions include changing the file system from NTFS to say ext3, but this would imply an edit to the grub file and another (fstab?) I believe. And also maybe reducing the old Windows partition to a very small size to make room for an increase in size of the Ubuntu partition. Although, note that partitions arrangements can take the unwary by surprise  - there are some restrictions in how partitions are used and these might possibly prevent an easy increase of size of your existing Ubuntu partition.

hth

---

### Post by anders_c_ on 2009-11-30
Does he really need to edit grub manually? wouldn't a simple "sudo update-grub" solve this after formatting?

---

### Post by QIII on 2009-11-30
I believe update-grub changes the mbr.  It gets its instructions from menu.lst (when using GRUB, as opposed to GRUB2), so menu.lst has to be updated.

---

### Post by anders_c_ on 2009-11-30
Arent you confusing update-grub with grub-install? Atleast it has worked for me to do an update-grub after installing/removing other Operating Systems...but that was grub2, perhaps its different with the old grub.

To Original Poster:
Is there any reason you have to stick with Jaunty? Backing up your data, removing both OSes and doing a fresh Karmic install will also solve your problem. Its a little more work than simply formatting windows though...

---

### Post by QIII on 2009-11-30
menu.lst applies only to GRUB.  GRUB2 does not use menu.lst.

---

### Post by Toke on 2009-11-30
I booted in windows and uninstalled some programs, then defragmented the drive.
Then rebooting with a mint 7 cd I spend a few hours moving the partitions leftwards, and now have 20G more for my linux drive.

It is not the perfect solution, but I am not sure what else to do.

---

### Post by flyfishingphil on 2010-04-02
HELP!!! Does anybody know of step-by-step instructions for a true Ubuntu Dummy regarding removing Vista and leaving just Koala on the drive without losing everything set up in Koala?

By step-by-step for Dummies I'm talking
Step 1 Turn on Computer
Step 2 Wait for computer to finish starting before doing anything else

I've been playing with Ubuntu and find it operating much faster than the Windough$ that came with the system but did a double boot. Have made all of the changes to Koala that I think I need and don't want to go back thru all of that again. (Don't remember everything I did and lost my notes.)

System is a Toshiba L350-S5933, 32 bit OpSys, ACPI x86 based, Intel Pentium Dual CPU T3400 @2.16GHz, 3.0 GB Ram, Bios Version 2.10. Did a full system of the Vista and files backup before installing the Koala on a Maxtor Onetouch 4 Mini w/160 GB. Also have Koala on a cd that works as a "Live CD".

Checked and Ubuntu opens the Maxtor with no problem.

Have seen references to Gparted, but need very simple step-by-step.

Do I need a boot disc for Koala? DO I have to make any changes in the partitions like format?

I don't speak "puter" just use it.

Thanks for any references to a set of instructions for Dummies.

Have looked at a couple of different books regarding Ubuntu but was wondering if something written in '06 still applies or has Ubuntu changed enough that the instructions would no longer be applicable? (Kind of like Windough$ 95 vs. Vista?)

Here's a new book on Ubuntu at [Barnes & Noble]("http://search2.barnesandnoble.com/BookViewer/?ean=9780672331091") that looks interesting. @ $50 it's still less than half of the cost of Windough$ 7

---

