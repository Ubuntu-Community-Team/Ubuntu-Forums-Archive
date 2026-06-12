---
title: "Deleted partition (ext4 -&gt; fat32)"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by xen0m on 2011-02-05
Hello.

I tried to create USB Ubuntu drive (on pen drive) and something wrong happened and (I assume) I formated my second (important) USB drive.

Before format, my disk had 2 partitions, one ext4 and one fat32.

After format there is only one partition, fat32 on whole drive. There are no files on it.

I have made the 1:1 copy of my drive with ddrescue. Now I try to recover my disk with Testdisk. When I use "Analyze" and then "Deeper search" the program finds my two previous partitions (ext4 and fat32), but if I want to list files on them, it is impossible for ext4. It says "Filesystem seems damaged". On the other hand files on "old" fat32 partition are listed properly. Unfortunately ext4 partition is far more important for me.

Is there any chances to recover my ext4 partition after format whole disk into fat32? Please help.

PS. If I use Photorec on that disk it recovers some files (I don't know if it recovers all files) but it is terrible to go through thousands of files with no directory structure and with random filenames.

---

### Post by oldfred on 2011-02-05
The formating may have overwritten just a little of the beggining of the partition, but that could be enough to cause damage.

The files are not totally random.  You do get file extensions. And some types of files you can recover file names. But it becomes a lot of work. I lost two folders an used testdisk. For example I had saved a text file many times. It recovered many versions. I am not sure I every recovered the last saved but between backup and several versions I was able to get most of my data back. Lots of grepping to search files.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by xen0m on 2011-02-05
Thanks for your answer and links!

But even if old partition ext4 is listed in Testdisk in "deeper search" it could be impossible to recover? There is no other way?

---

### Post by oldfred on 2011-02-05
I think I would try to recover if testdisk says it finds a partition. Whether all the data is there or not is another question.

---

### Post by xen0m on 2011-02-06
It looks like in screenshots. On r_testdisk1.png all partitions are listed. Old ones (ext4old and fat32 old). Files on fat32old are ok. I can easily recover fat32old partition.

But if I try to list files on ext4old partition it says "filesystem seems damaged" (as in r_testdisk2.png).

Is photorec my last option?

Would it be possible to recover ext4 partition (with directory tree etc.) in professional data recovery lab?

---

### Post by oldfred on 2011-02-06
I do not think the average lab can recover erased data. They pretty much are running testdisk type apps and do not want to spend the effort to recreate erase data.

 Your CIA or FBI may be able to check drive for edges of track and see if old info was still there. That worked better with old drives where writing tracks were larger and drives/heads were not as precise. Some may be able to check for residual data. Very expensive, so I would check prices before letting someone do it.

I used photorec and it recovers all recoverable files and parts of files. I had a text file I had saved many times and it found it many times. Drive was not full, so all the versions were still on drive. I had so many copies I was never sure if I found last saved or not.

---

### Post by oldfred on 2011-02-06
Some more links:

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)
sleuthkit is in repositories:
[http://www.sleuthkit.org/sleuthkit/](http://www.sleuthkit.org/sleuthkit/).

[http://www.linuxquestions.org/questions/linux-distributions-5/best-live-rescue-cd-for-ext3-data-recovery-417651/](http://www.linuxquestions.org/questions/linux-distributions-5/best-live-rescue-cd-for-ext3-data-recovery-417651/)
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by xen0m on 2011-02-07
Thank you very much one more time!

Using photorec I am able to recover many lost files.

I have one more question. Is it possible to somehow recover directory tree/filenames? Assume I **do not** want to recover files but I only want filenames and directory tree that were present on the disk before crash. Is there any way do do this?

---

### Post by oldfred on 2011-02-07
Filenames & directory structure seems to be the first thing lost. I do not know details.

Some more links with some detail. More for repair of damaged.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)

---

### Post by davidY on 2011-08-18
Same here!!! It turns out that the usb-creator, usb-creator-gtk will wipe your whole disk when you click the button. Even when your mouse is over a partition. I'm trying to run testdisk and photorec right now.

Edit: 2TB disk takes around 17 hours to finish on photorec :( .. now its 31 hours ..
Edit: I realized that photorec will fail on large videos - it is good at picking out the head of a file, but it will not follow the blocks to read the whole file. If your drive is fragmented most likely your large files will break half way through. 
Edit: I've switched to using testdisk
Edit: Test disk doesn't seem to work. My guess is if the root file system data is overwritten it won't be able to recover the partition. I'll run photorec to salvage the data and then try testdisk again to search for superblocks
Edit: Problem solved!
Solution:
* I used testdisk to find superblocks. 
* Select your disk, go to advanced, change the type to 83 (linux), then use find superblocks. This gives you a list of superblock offset. 
* Since i only have one hard disk this big I went with luck (and an acceptance of failure) to run sudo e2fsck -b [SUPERBLOCK LOCATION] -B 4096 /dev/sdxx. 
* If you have extra disk space you can image the drive and play with the images, if you do use images, you will need to use the loopback device or something. 
* I chose a large superblock offset location because I thought that the disk had probably been wiped only at the beginning. 
* It didn't fail on magic number test, so i crossed my fingers. the prompt asks yes/no, I just went with yes, no idea what happens if you press no
* At about step 2, it said [file name] has broken inodes I knew it was working. I copied the text for future reference, because these files are probably gone for good (or would require some more advanced technique to recover)
* I replugged the disk in and mounted it with sudo mkdir /mnt/tmp, sudo mount -t ext4 /dev/sdxx /mnt/tmp
* I saw that there were no folders, except for lost+found in the disk. (fear rising) I couldn't cd into lost+found folder (panic starting)
* I used sudo -i to get a root terminal, from there i could cd into the folder
* The folder names there were all like #93847430. I guess these are probably inode values. My guess is that ext uses two way pointers, one on each end, so we can reassemble the folder, but not the folder name.
* The disk counts as a 2tb unknown disk - I used testdisk to write the new partition structure. almost working

---

