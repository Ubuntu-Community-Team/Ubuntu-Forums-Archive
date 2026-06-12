---
title: "Installing Ubuntu on second hard drive."
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Rmc22 on 2009-04-03
I'm about to add a huge (1.5Gb) second HDD to my Win XP PC (250Gb HDD, NTFS), mostly to partition as NTFS for data storage.

But I'd like to install, or at least leave space for Ubuntu partitions on the second HDD.

My questions are:

1. When installing Ubuntu from the live CD (I did this about 2 years ago on an old PC) can I arrange for it to load Ubuntu from the second disk?  I guess some kind of bootloader will remain on the C: drive, would I be advised to allow Ubuntu to install its system installation on the C drive too?

2. Without going into too many options, how many & what size partitions would you create, given space is not an issue?  Some people seem to have suggested a 15Gb System, with Data(as big as you like), a 'small' home partition to preserve personal settings against future reisntallations, and a swap partition of 2 x RAM size.  Is all/any of this correct?

3. Can the live installation CD do all/any of this partitioning for me?  Or does it just put everything into one ext3 partition?

4. Does Ubuntu care about the various Primary/Extended etc partition options?

Not certain if I'm going to install Ubuntu immediately, but just want to leave space for enough future experimentation without wishing I'd left more for Ubuntu.

Thanks in advance.

---

### Post by billgoldberg on 2009-04-03
The partitions:

10-15gb for /root

swap isn't really neccesary if you have a lot of ram, otherwise double it

/home should be big enough to hold all your files.

On the live cd, there is a tool installed called gparted (alt+f2 -> gksu gparted) that will allow you to partition your harddrives.

The bootloader should be installed after installing Ubuntu and give you the option to either boot windows or ubuntu on startup.

---

### Post by Rmc22 on 2009-04-03
Thanks for the quick reply.

It'll be running with 3Gb RAM, if that confirms your comment re not needing a swap partition?  I also seem to read now that NTFS is not the problem it used to be for writing, eliminating the need for FAT32 partitions to exchange files with Windows.

Does it make any real difference if Ubuntu lives entirely on the second HDD?  And can 'gparted' also create a partion in unused space?  Initially, I'd like to create the non-Ubuntu partitions needed, then return later to install Ubuntu in the remainder.

---

### Post by wolfen69 on 2009-04-03
if you don't want to deal with possible grub issues, unplug your windows drive while installing ubuntu. most computers now have a quick boot option at start up allowing you to choose which drive to boot to.

and yes, that's what gparted is for, to create partitions. good luck.

---

### Post by Rmc22 on 2009-04-03
I had wondered if the BIOS screen boot options could do this, it's nice to know it can.

Loading onto a second HDD in the absence of the first Windows one won't cause any other problems when it's plugged back in then, just no boot loader on the C: (I assume) and something installed on the second HDD which BIOS can boot from, irrespective of Primary/Extended settings?

---

