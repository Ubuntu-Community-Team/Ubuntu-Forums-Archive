---
title: "Ubuntu 8.10 Formating"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by Bankai56 on 2008-12-31
I know this sounds easy for the most guys, but i am an absolute beginner.
So patients pls. :D
I upgraded ubuntu 8.04 to 8.10 through update manager and know 8.10 works like crap. (sorry developers)
In the Grub list it is still written 8.04 and nothing works as fast and neatly as it did in 8.04.
So does anybody know how to reinstall Ubuntu like windows. :D
So format all the data and delete every config and just install 8.10 from scrap.
And I also have Windows parallel installed. I can't delet that.
I am sorry if that makes it more complicated.
Thanks in advance:D
Bankai

---

### Post by jorj82 on 2008-12-31
Well, if you want to re-install 8.04 you will need the CD you originally used.  Just put it it the drive, restart your pc, and follow the instructions.  You've done it once already so it shouldn't be too hard.  Good luck! ):P

---

### Post by donkyhotay on 2008-12-31
If you're wanting to start over with a fresh install of 8.10 then you would first need to download/burn the 8.10 install CD and go through the installation process. Since it's a dual-boot you *probably* have the windows on NTFS with the old ubuntu on ext3 partitions (this is the most common setup but not certain so you should probably double-check). When prompted you would then want to reformat and then reinstall over the ext3 and not repartition since your partitions are probably configured the way you want them. Be aware if you do this that it will completely wipe out your current ubuntu erasing all data stored within it so if you have any important files there you will want to copy them to the windows partition first to keep them safe.

edit: this is assuming your not using wubi though which would mean you would then just uninstall from windows then reinstall with wubi again.

---

