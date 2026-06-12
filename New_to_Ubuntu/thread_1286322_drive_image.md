---
title: "drive image"
date: 2009-10-08
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-10-08
If I create an entire backup image of my Ubuntu system can I also keep other files on that external drive or does the image need to be the only thing on the drive? And does it matter what file system the image backup drive is in? Thanks all again.

---

### Post by rbc on 2009-10-08
If it is am image, yes, you can have other files in that partition. If it is a clone, no*. As far as the filesystem type, I don’t think an image file cares, keeping in mind the 4 GB restriction of a FAT32 filesystem.
*Cloning the entire drive to another drive will overwrite the partition table of the second drive, thus wiping out the partitions that were there. But, I have heard of folks cloning a mounted partition. Never had the guts to try it

---

### Post by cmcanulty on 2009-10-09
OK thanks I think maybe I am using old windows terms where if you image your C:/ you can reload an exact copy of OS in case of catastrophic failure. So for a similar safeguard for Ubuntu what is the best way and what program is best. I want to save the whole shebang to an ext HD in case of a disaster. Also does the ext HD have to be larger than my installed HD or just larger than the used part of laptop HD. The reason I ask is I have a 120GB ext HD I would like to use and my laptop has a 340GB HD but only less than 80GB is used.Ubuntu really need a program like system restore in windows that got me out of jams frequently.

---

### Post by alphaniner on 2009-10-09
[Partimage]("http://www.partimage.org/") which can be run from [SystemRescueCD]("http://www.sysresccd.org/").

---

### Post by HermanAB on 2009-10-09
Howdy,

I understand where you are coming from, but Linux is so much easier to re-install than Windows, that it really is only necessary to backup your data files.

If you screw up Linux, simply re-install the latest version - it only takes about 30 minutes, which is likely a couple hours faster than restoring an image.  Then you have the added advantage of having the latest and greatest version.

---

### Post by cmcanulty on 2009-10-09
OK thanks I have been backing up my documents (the only place I store files) but on linux I'm not sure how to back up all my add ons settings etc.

---

### Post by alphaniner on 2009-10-09
Restoring from an image takes a matter of minutes, definitely faster than a re-install.  And that's not even taking into account the time to configure a clean install.  Backup your documents and take an image of your root partition.

---

### Post by cmcanulty on 2009-10-09
OK what files should I copy to backup. So far I have just copied documents as that is where I save everything. But I'm not sure of the spots like software and settings on Ubuntu, in windows I knew where everything I should backup was.

---

### Post by alphaniner on 2009-10-09
It largely depends on how you have your system set up.  For example, I have a 15GB root partition and all my 'data' is on another partition.  So I make an image of my root partition, and all my system settings are saved.  Backing up my data is another thing entirely.  Most of it is replaceable, so I don't worry much about it.  The little that isn't I copy to a remote machine or burn onto disc.

In your case, if you only save your personal stuff in Documents then there isn't likely anything anywhere else.  Unlike with Windows you don't have write access to much outside of your home directory, so where else could stuff be? :)

---

### Post by achase79 on 2009-10-09
creating a image of /home will save almost all your program settings because they are saved as hidded files and folders in your home directory.

---

