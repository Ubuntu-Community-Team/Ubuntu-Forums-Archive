---
title: "How to format HD?"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by searcher1 on 2009-11-10
I run Ubuntu on an unpartitioned external hard drive. Ubuntu has just warned that there are many bad sectors in the hd. I am guessing this is due to a power failure while I was using the computer rather than an actual hardware fault. I have already backed up my data with the intention of formatting the hd and reinstalling Ubuntu. Can anyone tell me how to format the hd and how I can verify whether there really are bad sectors after the format? Thanks.

---

### Post by MelDJ on 2009-11-10
to format you must install gparted from the repo. it will be under system-administration

---

### Post by Lvcoyote on 2009-11-10
If windows is loaded on the internal hard drive of the computer, you can format it from windows disk management which is under control panel/administrative tools/disk management.  You should be able to go to the manufactuer web site of the hard drive thats your external drive and get a bootable utility that will check it for functionality.

---

### Post by jimmy the saint on 2009-11-10
Don't even worry about installing gparted.  If you are going to reinstall, the installer does all that for you.  You don't have to do anything but back up your data in order to prepare the drive, unless you want to partition the drive in a specific way.

---

### Post by searcher1 on 2009-11-10
Thanks for all the suggestions. I think I'll reformat the hd on Windows but I'll have to find a computer that has Windows first. I'll also do a chkdsk on Win for the bad sectors.

Once again, thank you all for the help!

---

### Post by jimmy the saint on 2009-11-10
Is there a reason you feel you need to reformat the drive in the first place?  Like I said, as part of the installation process the installer is going to format your drive.  Also, windows cannot format ext3/4 partitions, which means you will create a MS partition, only to erase it when you do the installation.

---

### Post by searcher1 on 2009-11-10
I didn't know that. I'll just do an install without the format then. Thanks!

Any way to check on the bad sectors? My HD is a Fujitsu and they no longer make hds so there is no more support.

---

### Post by peculiar penguin on 2009-11-10
[http://www.fujitsu.com/us/services/computing/storage/hdd/support/utilities.html#diagnostic](http://www.fujitsu.com/us/services/computing/storage/hdd/support/utilities.html#diagnostic)

---

### Post by searcher1 on 2009-11-10
Thank you so much for the link!

---

