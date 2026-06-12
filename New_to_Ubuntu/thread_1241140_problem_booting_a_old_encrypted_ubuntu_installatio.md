---
title: "problem booting a old encrypted ubuntu installation"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by gonzoga on 2009-08-15
Hey guys,

so heres the problem i have a old encrypted install of ubuntu with a encrypted home directory that i cannot access. The reason why is because i was stupid and installed a new ubuntu install on a different hd( assuming that grub would detect zed old install). now on the old ubuntu install grub is toast basically and i cannot boot into it. I can however open and access the old installation using cryptsetup. Now heres the real problem i forgot that i encrypted the home directory where all my files are at and i lost the passphrase. the fix ,i think, is setting up grub on the new install to boot also the old installation. I believe that this is the fix since i can still access the old install using the rescue mode on the ubuntu install disk.  I tried fixing grub that way but any option or guide i tried basically failed. anyways im on wits end on trying to fix this and kinda having trouble describing the problem. 
  oh so one thing that i did that got me i think close to fixing it was through the new grub install was this: I got access to the old grub menu.lst(from the old install) and copied the boot for the old ubuntu to the new grub menu.lst. The  error i got was number 17 when booting in grub. I found a guide online to fix that error by editing the fstab file. So what i did is copied the old fstab file info into the bottom of the new one. So all the info for both os's is still there. That didn't fix error 17.
anyways any help or suggestions would be much help.


Oh so one more thing that i think needs clarity: I cannot boot the old ubuntu install but i can access the files on the old ubuntu install. What i cannot access is my home directory on the old ubuntu install... i encrypted both the hd and my home directory. I have the passphrase for the hd but not the home directory....the home directory is where the files I want. I tried mounting the old home directory in my new ubuntu install but all i get is giberish which is why i think i have the incorrect passphrase for the home directory.

---

### Post by LewRockwell on 2009-08-15
place old ubuntu install hard drive in computer(without any other drive installed)

use SuperGrubDisk to see if you can correct your problems

[http://supergrubdisk.org/](http://supergrubdisk.org/)

.

---

### Post by gonzoga on 2009-08-15
Does work gives me a no kernel loaded error. I bet its not detecting it since the drive is encrypted :/ thanks though.

---

