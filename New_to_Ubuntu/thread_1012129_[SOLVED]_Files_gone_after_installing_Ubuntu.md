---
title: "[SOLVED] Files gone after installing Ubuntu"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Torrot on 2008-12-15
Hi, I'm new to Linux, I have installed Ubuntu 8 from live CD and due to lack of HD space I had to install it into existing Fat32 partition. I don't remember Ubuntu installer telling me that it would format the partition or erase anything (I thought it would just use the needed space, like windows would do and leave all other files alone), but looks like I can't access the data that was on that disk anymore. In fact this disk isn't accessable from windows anymore at all. And I can't find the data when booted to Ubunto too, so looks like the data is gone.

Can I do anything to restore the data?

---

### Post by Songwind on 2008-12-15
Unfortunately, no.  If you formatted the drive, it's pretty much gone.

---

### Post by Michael.Godawski on 2008-12-15
> Hi, I'm new to Linux, I have installed Ubuntu 8 from live CD and due to lack of HD space I had to install it into existing Fat32 partition. I don't remember Ubuntu installer telling me that it would format the partition or erase anything (I thought it would just use the needed space, like windows would do and leave all other files alone), but looks like I can't access the data that was on that disk anymore. In fact this disk isn't accessable from windows anymore at all. And I can't find the data when booted to Ubunto too, so looks like the data is gone.

Can I do anything to restore the data? 	

I am afraid no.
When you are in Ubuntu please run this terminal and post the output here:

```
sudo fdisk -l
```
Type in your password when needed and hit enter.

---

### Post by Viranh on 2008-12-15
I managed to recover files from a FAT32 flash drive that I formatted once (it came with U3 software and when my boyfriend plugged it in and found it he kindly formatted it for me to get rid of the stuff so it didn't install on his computer). I didn't get them all back, but I got 60% of them or so. I used photorec. It says it works on drives that have been formatted.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

For Linux, install with:
```
sudo apt-get install photorec
```
There's a download link for windows in the wiki's. I'm unsure where you'll have to run it from because I'm not sure an ext3 partition will be visible from windows to this program.

Try not to write anything else to the partition you want to recover data from. You may still have some recoverable data, although you will definitely lose some. Remember in the future to ALWAYS back up data when messing around with your OS's.

---

