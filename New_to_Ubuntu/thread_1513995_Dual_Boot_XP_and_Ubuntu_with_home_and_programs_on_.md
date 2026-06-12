---
title: "Dual Boot XP and Ubuntu with /home and programs on secondary drive"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by tempmike on 2010-06-20
I have a 160gig drive that I've partitioned into thirds (NTFS, EXT4 and unformatted) with a fresh installation of windows XP on the drive. Also I have a 500 gig drive partitioned into fourths (NTFS, EXT4, FAT32 and unformatted) which I intend to use for my programs, files and swap space (nothing on it yet)

I'd like to install the system files for Ubuntu on part of the 160 drive and then keep programs and user settings on part of the 500 drive

It may go without saying but I'm pretty green using Ubuntu so detailed instructions would be great. About all I've understood so far was to install windows first so it doesn't break the bootloader.

One final note: this is a new machine where I just installed windows so I have no worries about messing everything up and reinstalling from scratch. But I'd like to avoid this.

Thanks for the help.

---

### Post by Merk42 on 2010-06-20
I really don't see a reason to separate your programs from Ubuntu, given that most (if not all) of the programs you would use are free and probably included on the CD.

If you want to just separate /home (which contains stuff like documents and well as settings for programs) from Ubuntu and its programs (as well as future programs) do the following:

Insert the CD, and restart the computer booting from the disc (do not run it in Windows)
Install Ubuntu 10.04 and when you get to step 4 choose "Specify partitions manually (Advanced)"
Find the partitions you want to use, make them ext4 and whatever partition you want to be Ubuntu and programs mount a /; whatever partition you want to be the user settings mount as /home

---

### Post by tempmike on 2010-06-23
Sorry about the delay in responding.

I need to install programs separate for disk space mostly. Also most of the programs I'll be using are not on the install disk and most are not free either. For example I can install R (a statistics program: [http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)) fine but I'm pretty sure it installs onto my system drive whereas I'd like to install onto a second disk.

I'm really in the dark on how to change where that apt-get thing installs programs or how it works in general so any help on either front is greatly appreciated.

---

