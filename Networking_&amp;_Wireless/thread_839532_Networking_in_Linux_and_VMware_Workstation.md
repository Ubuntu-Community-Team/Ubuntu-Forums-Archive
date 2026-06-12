---
title: "Networking in Linux and VMware Workstation"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by kriemer on 2008-06-24
I am not sure if this is a networking post or a post more appropriately assigned some other area of the forum.

I am looking forward to using Linux in place of WinXP but for arcane reasons I want to be able to continue to run in WinXP as well.  To do this the virtual machines (all WinXP) have to be in EXT3 partition (Linux VMware 64 does not run them from a NTFS formatted location) but the data that the VM's address can remain, and needs to remain on an NTFS formatted drive (Data is highly volatile while the VM configuration is not.  So if I want to be able to run either in Win or Linux the data needs to remain in a drive format that is accessible to both).   The NTFS disk holds a "Virtual Drive" that one VM is connected to, a second VM connects to this drive through the Windows network.

My problem is giving Read/Write permission to the Virtual Drive connected to the 2nd Windows VM.  I can see the drive, I can open the drive, I just can't access any of the directories of files. This is not a problem when running from a WinXP host machine but it is a problem running from the Linux host.  I have tried to set a Samba share for the virtual drive but can't do this either.

So far I have done the following (some steps easy and obvious, some less so):

   1. Ubuntu 8.04 64 bit is installed (dual boot) and updated
   2. Installed VMware
   3. Added a 64bit library to allow VMware to run
   4. Installed Gpartition (Linux Partition manager)
   5. Formatted 1 drive to EXT3 (for my Virtual Machine files)
   6. Gave all drives read/write permission: sudo chmod -R 777 /Media/
   7. Renamed EXT3 formatted Hard Disk: sudo E2label /dev/Device Name New Label (16 characters max)
   8. Installed (GUI disk manager) pysdm; simple way to define Hard Disk as auto mount

Any thoughts, or too poorly written to understand the problem?

Thanks

k

---

### Post by kriemer on 2008-06-26
And so in the end the problem had nothing to do with either Linux or VMware specifically.  To gain access frmm the 2nd Virtual Machine to the Virtual Drive connected to the 1st Virtual Machine I needed to set the Windows share permission to "Everyone" in the Virtual Disk.  

Odd that this does not need to be done in the Windows Host configuration, but no big deal at all.

---

