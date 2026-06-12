---
title: "Issues with second hard drive"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by RuneGeek on 2009-08-11
Been poking around the existing threads on second hard drives but I've yet to find an answer to this one.

I am running Jaunty and I had been dual-booting XP off a secondary HDD.  Given that I never use XP anymore it had become a waste of disk space so I reformatted to ext4 using GParted and then used Mount Manager to mount it to "/".  This of course changed my fstab file; I looked at it and it looks okay to me.  

I rebooted and didn't see any errors but I also don't see any indication that the new drive is being used.  I thought by mounting the new drive (sdb1) to "/", same place as the original Ubuntu drive (sda1) was mounted, that it would all just kind of get pulled in together and I'd see more free space in the File Browser.

I'm still pretty new at this.  :)

---

### Post by Ocxic on 2009-08-11
mounting the drive to / will not increase the amount of space on your computer.
you should mount the drive to /media/Storage as i do, of course you can pick a name other then storage.

if you want to connect the 2 drives and make them act as one big drive look into RAID 0/stripping, but setting that up will prolly require a re-install with the alternate cd or you will have to resize your current partition and setup a raid array manually with mdadm.

---

### Post by RuneGeek on 2009-08-12
Okay, I follow you.  Went back and re-read some threads ([this one]("http://ubuntuforums.org/showthread.php?t=38062") in particular) and I see now where I was misunderstanding.

Got it to work under /media, but I'm not sure why I couldn't get it going under /mnt like the one in the aforementioned thread.  Guess I need to keep reading.  :)

---

### Post by Ocxic on 2009-08-12
you'll just need to give your self ownership of the mount point

eg: "sudo chown username:group /media/Storage"

for me it would be "sudo chown ikrel:root /media/Storage"

---

