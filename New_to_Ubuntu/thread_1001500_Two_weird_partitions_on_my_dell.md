---
title: "Two weird partitions on my dell"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Eggbertx on 2008-12-04
I am going to partition my drive to put intrepid on it to dual boot with windows. Along with the windows partition there are two small ones. I know ones for backups because Dell is two cheap to include a backup cd, but which is it and what is the other?
Order of filesystems

Fat16
Ntfs (Winblows)
fat32

Which fat filesystem is the backup, whats the other and how do I burn the backup to a dvd so I can delete that partition to make room for Ubuntu?

---

### Post by SIGTERMer on 2008-12-04
I use toshiba, but i think you're problem is similar to what i encountered..

1: before anything, make a backup DVD/CD. Dell should include a utility to burn a system restore disk.. at least mine did.
2: to check which is which, refer to the laptops documentation or search the dells site. OR use your live CD to mount the partitions (using nautilus, if you prefer) and check for your self.

personally, my system restore disk had an option of installing the entire system into one partition only (including backup and the other one). but you have to re-install windows. and that was for toshiba, i have no idea if the disk you burn has the same future :)

---

### Post by goldenphoenix713 on 2008-12-04
> **Eggbertx said:**
> I am going to partition my drive to put intrepid on it to dual boot with windows. Along with the windows partition there are two small ones. I know ones for backups because Dell is two cheap to include a backup cd, but which is it and what is the other?
Order of filesystems

Fat16
Ntfs (Winblows)
fat32

Which fat filesystem is the backup, whats the other and how do I burn the backup to a dvd so I can delete that partition to make room for Ubuntu?

Here's something I was able to find.  Hopefully, it answers your question.
[http://www.bay-wolf.com/harddrive.htm#23](http://www.bay-wolf.com/harddrive.htm#23)

---

### Post by falcon61102 on 2008-12-04
The first partition at the beginning of the drive is the Dell diagnostics and recovery programs.  It's recommended that you leave that one alone as it contains info about your computer as well as the programs to restore it if necessary.  That and people have had issues after messing with that partition.  

The NTFS as you stated is your Windows partition.  

And the final partition is the Recovery partition.  If you can view that partition in Windows, you can theoretically burn it, but you may run into some access errors.  Besides burning a copy of it, you can pretty much delete this partition or resize it at will without causing any major issues with your computer.  This partition is normally anywhere from 6-10gig.  

Depending on how old your computer is and what type, you may have an additional small partition on there for the Dell Media Center.  The only problem people have run into with messing with that partition is if they have a button for the Dell Media Center on their keyboard.  Apparently if you press the button after deleting that partition you can generate some errors.  You can also use that partition/button for a dual boot setup.

---

### Post by mapes12 on 2008-12-04
If you're looking to make a mirror image of your current system before embarking on your Ubuntu installation I can recommened [Driveimage XML]("http://www.runtime.org/driveimage-xml.htm"). It's free and IMHO better than Ghost.

For more guides and tutorials on installing and running Ubu take a look at the link in my sig file in red, below.

---

