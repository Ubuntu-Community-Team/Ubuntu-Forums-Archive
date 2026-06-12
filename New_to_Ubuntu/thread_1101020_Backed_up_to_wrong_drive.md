---
title: "Backed up to wrong drive"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Traprock on 2009-03-19
Hi all,
I am on the new to Linux one step forward two steps back treadmill. Sorry to be so long-winded, but I hope  the errors are obvious if I describe my procedure. I assume the basis of my problem is adapting the linux file structure vs a disk-based structure.

I have installed Ubuntu 8.10 to function as a small network fileserver and backup. I installed Ubuntu to a small 20gb disk, 2 partitions sda1, sda5. Got Samba happening. 

Installed data disk 4 partitions sdb1 (label 'MyDocuments)sdb2,3,4. Installed backup disk 4 partitions sdc1 (label MyDocsBackup),sdc2,3,4.  Eventually got all the partitions on the data disks mounted, loaded data into MyDocuments. 

Got ugly when I tried to back up to the backup disk MyDocsBackup via grsync (not its fault, it looks like a good thing). The backup somehow went on the little system disk, choked it out. Subsequent backup attempts gave disk full errors. I unmounted and remounted all, same deal. I put a folder 'Backup' in the backup directory, and the backup worked. However I cannot set up shares on any of the other partitions as I get directory full errors. 

A fundamental issue is using file mananger I cannot even see anything on the system disk. 
What do I need to do to show the data, so I can delete it? 
What errors have I done in mounting that won't allow me to access sdc, but seem to keep pointing to sda? Everything in fstab looks right to me, but I only know where the contents of disks/partitions by looking in gparted. Any advice appreciated.

Solved-if anyone has similar issues check this excellent explanation and solution.(thanks drs305 for link)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

