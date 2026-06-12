---
title: "Reusing USB External Drive"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by colintivy on 2009-12-07
Hi Folks

I have been posting about a 2 1/2" external HD not being recognised by Hardy. I now have 3 1/2" HD in an enclosure which was used to back up a Win98SE system. I now want it for backing up my /Home directory. On trying to look at it, I find all the Win guph all right and have cleaned it out. However it comes up the the "Cannot Mount it" panel, this is because it must not have been shut down properly originally.I am given two brief options playing with the /etc/fstab file to correct this but am a bit cautious about doing so without step by step advice. Because the original file system was Windows based I feel that I ought to format the drive into at least ext3 (or should it ext4 for 10.04?) as well. Any advice or reference to existing helpful texts much appreciated.

colintivy :confused:

---

### Post by zkriesse on 2009-12-07
You can use a program called, Gparted or Gnome Partition Editor. You can install it via Applications Add/Remove depending upon the Gnome Version you're using. Note: I'm only saying that as you mentioned formating the drive I believe.

---

### Post by teward on 2009-12-07
One way to make the old Windows file system go *WHOOSH" is to format the drive.  You can do that with gparted extremely easily.  Depending on formatting though, Winblows would format it as either NTFS or FAT16 or FAT32, and that might screw with your system a bit.

---

### Post by colintivy on 2009-12-08
Hi you two!

Yes, GParted will be of use when I manage to Mount the drive. The problem is that it shows as being in use and therefore inacessible. The cures shown on the "Can't Mount" panel are incomplete and I have not fully understand them...all because I am too inexperienced. I do not have a Windows machine to close the drive down properly and the delving into the odd lines lurking in mine is a bit dounting. Perhaps someone will advise?

colintivy :confused:

---

### Post by zkriesse on 2009-12-08
> **colintivy said:**
> Hi you two!

Yes, GParted will be of use when I manage to Mount the drive. The problem is that it shows as being in use and therefore inacessible. The cures shown on the "Can't Mount" panel are incomplete and I have not fully understand them...all because I am too inexperienced. I do not have a Windows machine to close the drive down properly and the delving into the odd lines lurking in mine is a bit dounting. Perhaps someone will advise?

colintivy :confused:

Ok so the drive is being shown as mounted on the Ubuntu DE (Desktop Environment)? And you are trying to Unmount?

---

