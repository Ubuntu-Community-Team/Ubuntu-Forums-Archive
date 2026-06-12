---
title: "Windows 7 not seeing files"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by littledude565 on 2010-02-28
I have three partitions on my laptop (Ubuntu, Windows and a 24gb NTFS one)
I copied all my music onto that 24gb partition from my ubuntu drive, but under windows i cant see any files in it. It just appears to be empty. Anyone know whats going on, and how i can fix it?

Thanks for any input

---

### Post by asmoore82 on 2010-02-28
Have you went back to Ubuntu to make sure the files are really there?

If so, is your Windoze set to not show hidden files, system files,
or whatever-else they might have made up for 7?

---

### Post by Joe Ker1086 on 2010-02-28
When i was using windows 7 and fedora windows 7 wouldnt even open ext3 partitions. not sure about ext4 tho... in fact it wouldnt even let me delete or resize anthing that wasnt fat or ntfs...

---

### Post by Arkitekt on 2010-02-28
Windows natively does not support filesystems other than FAT and NTFS, but the OP stated that the 24Gb partition was NTFS.

I agree with asmoore82, check to see if W7 is able to see hidden files, and double check via Ubuntu to see if the files are indeed there.

---

### Post by Mark Phelps on 2010-03-01
In Win7, type Disk Management into the text entry box after clicking the Windows Logo button.  That will open up the Disk Management panel.  Look at the top columns for Capacity, Free Space, and % Free.

If the partition in question says 100% free, the files are NOT there.

If it's less than 100% free, they're hidden for some reason.

---

