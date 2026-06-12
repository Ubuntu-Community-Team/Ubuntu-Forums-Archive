---
title: "I Deleted NTFS partition and reformatted disk as ext3 in error"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by wyatt roberts on 2009-12-26
I was trying to make the jump to Linux finally, but...It was the middle of the night, the two disks were the same size and I was trying to format my new drive as ext3.  I bought it new and when I saw NTFS I used either GParted or Palilmpsest disk utility to delete my NTFS partition and formatted my data disk as ext3.  I haven't stored anything on the disk since and from google-ing the question I am under the impression I still have the information there but while there are a variety of programs advertised that might fix the problem I am unsure which ones work and am worried if I do this wrong I will lose what I may still have if I can get to it to get it back.  I looked at sysrescue and burned a disk but once booted it I haven't a clue how to proceed with the sysrescue.  I have played with the live CD for a while but really don't know what I'm doing with Linux yet.  Being afraid I might make the wrong choice, I did go out today and get a new esata thinking the safest approach would be to clone the diskand make my attemped rescue on the clone but, once again, I really don't know how to clone the reformatted ext3 disk.  I thought I was following the article's instructions but had the separate NTSF mounted to record what I was doing so I could save time when I had to retrace my steps.  I'll just use the live cd's installer next time.  If anyone could explain what I need to do to rescue the information on the esata drive I deleted the NTFS partition and reformatted as ext3... I would truly appreciate it.
Thanks.  Wyatt

---

### Post by taurus on 2009-12-26
Maybe this is what you want/need/hope.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by wyatt roberts on 2009-12-26
> **taurus said:**
> Maybe this is what you want/need/hope.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Thanks,  I am going to the site now.  Hope is about right...
Thank you.
wyatt

Is there some preferred method to clone the problem disk and try to rescue the clone so as to not lose the opportunity to retry the rescue if something goes wrong with the first attempt?

---

### Post by wyatt roberts on 2009-12-28
I installed the package gddrescue.  I used it to make a copy of the disk in question. That took a while. I installed the package testdisk.  I ran test disk.  It found an invalid FAT boot sector, that no partition was bootable, and when I hit analyze it found the primary bootable Linux partition that I created over the original NTFS partition that I deleted and then created the primary bootable ext3 Linux partition.  I know that I am working on a copy of the data but it took about 18 hours to create the copy so I am hoping that someone with some experience with testdisk can tell me if I now need to use "T: change type" to change it to NTFS.  So, if you have used testdisk and what I need to do is use "T: change type to change it to NTFS I'd sure appreciate the advice.  The attached TestDiskTtoChange.jpg shows the disk in question (as copied by ddrescue, in Gparted, and 3 screens, first in lower right corner, second in upper right and finally, the decision point fo T: change type on the left below the Gparted screen.   wr

---

### Post by wyatt roberts on 2010-01-01
FWIW: I reasoned that if there was a solution that likely it would bemore likely (just percentage wise) from a windows world source since I was trying to recover files from a windows formatted (originally) drive.  I realize this might be an assuption in error.   I used a windows world program: GetDataBack and recovered about 1/7th of the disk.  I downloaded and tried another windows world program: R Studio in Trial-ware mode and it didn't do as well.  I only have limited time and plan to see what TestDisk can do at some date, but I have to give up what little time I have to see that and I am busy learning Linux for now. Disk recovery is now on my list for later. What I have done is install MondoRescue from Synaptics and HAVE successfully backed up but haven't tried restore yet.  I tried Mondo a month or so ago and it wasn't working with Ubuntu then.  It is, apparently, now.  It was an expensive lesson.  Not in software cost, but in lost files.  SO... I will be trying the baremetal restore of Mondo soon. And that is the rest of the story.  Some things cannot be solved and apparently reformatting a drive can be only 1/7 th solved unless you have a backup...
wr

---

