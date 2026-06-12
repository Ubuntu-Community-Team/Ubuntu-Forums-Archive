---
title: "What partitions will the Live CD create?"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Rmc22 on 2009-04-05
If I run the Live CD to install Ubuntu, and point it at some unallocated space on a second hard drive (there's about 100Gb of it), will it create just one partition, or additional ones for documents, swap, etc?

If it just uses the whole 100Gb by default as one partition, I'm assuming that I can manually divide that up later with 'gparted'.  If so, what would you suggest I create for best results?

---

### Post by kestrel1 on 2009-04-05
You can manually partition the drive during the install process. By default Ubuntu will create two partitions one for SWAP & one for the system '/'
I would suggest creating a '/home' partition as well

---

### Post by Rmc22 on 2009-04-05
Would I be right to assume that it'll set about 15Gb aside for the system, one twice the RAM for swap, and that I should assign all the rest to /home?

And will I run into any potential 'maximum of 4' primary partition problems, or does it make them extended or does this not apply?

---

### Post by kestrel1 on 2009-04-05
You can make all the partitions extended. The sizes you say sound about right, but if you have a large amount of RAM I wouldn't make SWAP any more that about 2GB unless you use hibernate, in which case make it about 1.5 times your ram.

---

### Post by Rmc22 on 2009-04-05
OK, I've two primary partitions already on the HDD, so suppose the new ubuntu ones will need to be extended.  I'm guessing they need a drive letter, or at least the /home one will, if I'm ever to try accessing the data from windows?

My RAM is 3Gb, is more than twice that as swap pointless, or bad in some other way?

---

### Post by gandaran on 2009-04-05
> And will I run into any potential 'maximum of 4' primary partition problems, or does it make them extended or does this not apply? 
yes if you already have more than one windows partition on the hard drive, make one extended partition then install ubuntu's /root, /home and swap  partitions on the extended partition.
when installing choose the manual partitioning process, you'll find it easy to make the partitions.

---

### Post by kestrel1 on 2009-04-05
I wouldn't have 6gb SWAP. I would go with 3.5gb max & even that might be overkill.
Linux does not use drive letters like Windows. You need to think differently when using Linux.
You wouldn't gain access to Linux drives from Windows, but you can access the Windows drives from Linux. However I believe there is a program that will allow access to Linux drives from Windows, but I can not remember its name.
If you have two primary I would go with the third one being an extended & creating logical drives for Ubuntu in there.

---

### Post by hessczoo on 2009-04-05
Well the default partitons Ubuntu wanted to make for me were:

12GB for swap and the other 280ish GB for the /

I would say the default will probably work fine for a basic setup anyway.

---

### Post by Rmc22 on 2009-04-05
I assume gparted will turn the unallocated space into an extended parition for me?

And if Linux doesn't use drive letters, will all the ubuntu partitions be effectively invisible to windows, and not affect existing/future drive letters under windows?

And would you let the installation CD put a bootloader on the C: drive (windows) or else just use BIOS options to direct it manually to the second drive, or is this not possible if ubuntu's in the extended partition?

---

### Post by hessczoo on 2009-04-05
When you install Ubuntu it makes your boot loader turn into GRUB. And GRUB is far more appealing than the Windows boot loader, trust me. It looks neater, and works great. I don't think Windows will pick up your Linux partiton, but I don't use Windows so I wouldn't know for sure. Gparted can indeed partiton your drive, but the Ubuntu installer can as well.

---

### Post by oldos2er on 2009-04-05
I believe you'd need to run 'Manual' installation to create a partition from unallocated space.

 Windows can't natively "see" an ext3 partition (assuming that's the file system you'll be using); it doesn't really have anything to do with drive letters.

 By default Grub will install to the first hard drive's MBR.

---

