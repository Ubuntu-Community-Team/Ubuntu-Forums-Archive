---
title: "Recovering files from accidentaly formatted partition"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Hermansuco on 2011-06-17
Any suggestion or comment would be greatly appreciated...

I inadvertently formatted the partition where windows xp "was" installed. Ideally I would like to undo the formatting and re-instate all the files. The partition is fine and still there... but "empty". If undoing the formatted is not possible then I would like to recover as many personal files as possible. As you would imagine, most of my life was in there. I am going to use TestDisk in an attempt to "recover" the partition, though the partition is there.
I've never attempted anything like this before, so any word of advice is welcome.

---

### Post by crispy_420 on 2011-06-17
There are several posts ongoing for the same topic, here is one:

[http://ubuntuforums.org/showthread.php?t=1784235](http://ubuntuforums.org/showthread.php?t=1784235)

---

### Post by blackmail on 2011-06-17
Been there done that it is a very nasty job, anyway what the actual procedure is:

-Try Hiren's Boot CD or DVD - you can download them [http://www.hiren.info/pages/bootcd]("http://www.hiren.info/pages/bootcd") also they have a thread on data recovery [here]("http://www.hiren.info/downloads/data-recovery/hard-drive/1")

If all of this fails, well then go the opposite way, but i suggest taking the Hiren's boot cd/recovery tools journey, since then you will see what actually happens and usually they have a high rate of success


-Use windows for the job (sorry linux users that's the truth)

-Put the HDD in another computer and try to make an image of the partition

-There are several programs capable of doing that even on windows :)

-Search for a program that would be suitable for you to do the job on windows

Hope this helped..

Regards,
Blackmail

---

### Post by coffeecat on 2011-06-17
If you are not successful with [s]photorec[/s] testdisk in getting the actual partition back, the application photorec (which comes with testdisk) can be used to recover certain types of files. Here is a useful link which tells you how to use both:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

The photorec instructions are about two-fifths of the way down, and there are also instructions for using two other data recovery utilities, foremost and scalpel.

---

### Post by crispy_420 on 2011-06-17
coffeecat I thought it was the other way around. 

testdisk = partition recovery
photorec = file recovery

---

### Post by coffeecat on 2011-06-17
> **crispy_420 said:**
> coffeecat I thought it was the other way around. 

testdisk = partition recovery
photorec = file recovery


Oops.... One mistake. Sorry. That should have been, "If you are not successful with **testdisk** in getting the actual partition back." Thanks for pointing that out. I've corrected the post, leaving the original error in, struck through for the record. The rest is correct - I hope! :)

---

### Post by doas777 on 2011-06-17
@op, 
if you just formatted over it and have not written any data to it, I would expect TestDisk to work great for you. just make sure you are writing the recovered partition out to a different drive//partition than the one the data was lost off. otherwise the first bit of data you recover will overwrite other bits of data, preventing them from being recovered.

---

### Post by Hermansuco on 2011-06-17
Thank you to all for replying! 

I will be reading today and maybe tomorrow as well before attempting anything. I am currently using the Ubuntu partition to access Internet assuming that, since windows was installed in the other partition (dual boot machine), it should remain untouched by Ubuntu (hoping this assumption is correct). I will follow the advise of getting another hard drive to  create an image in and play with without fear of causing more damage.

Once again thank you, and I will keep you posted during the process.

---

### Post by blackmail on 2011-06-19
> **coffeecat said:**
> Oops.... One mistake. Sorry. That should have been, "If you are not successful with **testdisk** in getting the actual partition back." Thanks for pointing that out. I've corrected the post, leaving the original error in, struck through for the record. The rest is correct - I hope! :)

Regarding photorec:
-Good part: It tries an OS/FS independent recovery;
-Bad part: There are many fragments on a HDD usually, and especially on a windooz partition, and so the recovered files have a very low chance of working, anyway that's how it was when i used the program last time, maybe this was corrected, since that was a few years ago :D

---

### Post by Hermansuco on 2011-06-20
I've tried to install TestDisk in Ubuntu but the application didn't run. I will be installing it in a Windows machine. then, I will remove the hard drive with the partition I need to recover and will try to copy the image into an external hard drive...

---

### Post by Hermansuco on 2011-06-21
After 12 hours creating the image and 4 hours checking files I finally got 223 segments. I will try to recover the partition tonight.

---

### Post by Hermansuco on 2011-07-01
[]("http://ubuntuforums.org/showthread.php?t=1784873")[]("http://ubuntuforums.org/showthread.php?t=1784873")I am following the instructions in cgsecurity.org/wiki/TestDisk_Step_by_Step and when I got to pressing "p" to list "my files" this is what I got in return in bold red letters:

[URL="http://ubuntuforums.org/showthread.php?t=1784873"]http://www.cgsecurity.org
   * FAT32 LBA                0   1  1 42542 198 15  683449656 [New Volume]
Directory /

drwxr-xr-x     0     0     16384 21-Jun-2011 06:38 _278052_
drwxr-xr-x     0     0     16384 21-Jun-2011 06:38 7b03a8e104ae0d6cb2b20671

[/URL]
Since there are not images or mention anywhere in the document about getting this in return, I am going to go back and do a "deeper search" to see if I can get any files name. 

This is what my previous screen looks like:

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1 42542 198 15  683449656 [New Volume]
P Linux                42542 208 35 60054 198 48  281329664
P Linux Swap           60054 231 18 60801  47 30   11988976


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,

---

### Post by Hermansuco on 2011-07-01
What would this mean?... 


TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 500 GB / 465 GiB - CHS 60802 255 63

The harddisk (500 GB / 465 GiB) seems too small! (< 565 GB / 526 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
  Linux                51176 171  4 68688 161 17  281329664
  Linux                51185 151 39 68697 141 52  281329664
  Linux                51188 231 52 68700 222  2  281329664



[ Continue ]
EXT4 Large file Sparse superblock Recover, 144 GB / 134 GiB

---

