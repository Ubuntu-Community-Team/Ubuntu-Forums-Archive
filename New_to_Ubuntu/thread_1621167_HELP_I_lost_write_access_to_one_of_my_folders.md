---
title: "HELP I lost write access to one of my folders"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by sarc on 2010-11-13
Suddenly one of my folders on external USB drive shows as read only.  SUDO chmod 777 /path does not do anything: I can see the disk is being accessed but when I click on the files they are all still read-only.  Same for gksudo Nautilus and change permissions thru GUI.

How can sudo chmod not work????  Or is it another problem not originating from read/write privileges?  HELP...

---

### Post by diablo75 on 2010-11-13
I don't have a solution but just wanted to ask what filesystem the USB stick uses?  FAT32?  NTFS?  ext3/4?  I'm curious.

---

### Post by jrev on 2010-11-14
copy this folder to your hard disk and then you'll be able to correct its permissions
if your USB key is fat32 then the permissions are not recorded

---

### Post by Crusty Old Fart on 2010-11-14
Another possibility is that you may have lost ownership.

The following command will give ownership of ******[COLOR=Green]foldername[/COLOR]** to: [COLOR=Blue]**yourusername**[/COLOR]
recursively ([COLOR=Red]**-R**[/COLOR]), meaning the directory and all of its contents including all subdirectories and their contents. (See: **man chown**, for more help)
```

sudo chown **[COLOR=Red]-R[/COLOR]** **[COLOR=Blue]yourusername[/COLOR]** **[COLOR=Green]foldername[/COLOR]**

```

It may help us figure out exactly what's wrong if you could post the output from the following command so we won't have to continue guessing:
```

ls -ld **[COLOR=Green]foldername[/COLOR]**

```

---

### Post by sarc on 2010-11-14
Thanks to all, I'll follow your advice.
Yes it is FAT32 to share files with my work computer Vista (God I hate that P.O.S.)

I suspect corruption of my Fat32 volume it was an encrypted hidden volume might have had some parts overwritten by mistake.

Will try and report back!

---

### Post by sarc on 2010-11-14
I think it is a case of corrupted FAT32 partition... seems like the case below.  This would explain why Nautilus gives me a read-only status although FAT32 does not even support it.

I'll try the fix.:guitar:

gifford.scott
First Cup of Ubuntu
 
Join Date: Dec 2009
Beans: 5
	
Re: USB thumb-drive (fat32) read only
I recently ran into a similar problem when I accidentally pulled out a VFAT-formatted USB drive w/o unmounting it. In my case, the issue was that the USB drive now had a corrupt FAT, and when the USB drive was inserted, the Nautilus file GUI was silently marking the drive as read-only to prevent further writes to the corrupt FAT.

The fix:

With the USB drive plugged in, unmount the USB drive (right-click on the drive icon on your desktop and select 'Unmount') and bring up the GPartEd partition editor (System->Administration->GPartEd). Under GPartEd, select the USB drive (typically, /dev/sdb) in the upper right-hand pull-down list. If you've chosen the right drive and it's unmounted, you can right-click on any of the partitions listed (typically, only one: /dev/sdb1) and select 'Check' to perform a filesystem check on the partition. Running a filesystem check should correct the FAT on the drive partition - just pull-out and reinsert the USB drive and it should be restored to read-write.

---

