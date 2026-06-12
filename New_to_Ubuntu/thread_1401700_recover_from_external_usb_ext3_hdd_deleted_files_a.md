---
title: "recover from external usb ext3 hdd deleted files and folders"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by Claus7 on 2010-02-08
Hello all,

I encountered a terrible problem lately by not being able to see some data (files and folders) in two specific sub folders of an external usb hdd formated as ext3.

I suppose that the data are removed accidentally with some rm -rf command or by pressing the delete button or they are impossible to be seen for some unknown reason. 

The hdd is bought in 2009 so if I type ls -l I get those two folders in question with this information:
drwxr--r--  2 user user  4096 **2007**-10-30 18:34 folder_name

It is impossible to see such a name for a folder as the disk is much newer than 2007 and also the folders where created at most four months ago (that is inside 2009).

I have come across multiple solutions, yet most of them refer to data being recovered from damaged partitions or partitions that accidentally where overwritten. 

I would be more than grateful if someone was able to shed some light on the issue.

Regards!

---

### Post by Claus7 on 2010-02-08
Hello,

searching about the issue I came accross [ddrescue]("http://www.gnu.org/software/ddrescue/ddrescue.html"), which I suppose that might do the trick.

The thing is that I do believe that the missing files are there since the difference between the used space with df -h command, and the one I get just by right clicking and enclosure all the folders and hit properties is more or less 100GB! I guess that there is something fishy here...:-k

Regards!

PS: Any advice on the issue as well as any information about ddrescue from users who have used it in the past, will be most welcome!

---

### Post by mechro on 2010-02-08
I can't advise re ddrescue but you could try **testdisk**.

Although testdisk is primarily a partition recovery tool it can also find and copy deleted files. Install it via synaptic and start it with **sudo testdisk**.

Before using any recovery tools you should back up your important data in case anything goes wrong.

---

### Post by Claus7 on 2010-02-08
Hello,

first of thanks for the response and the advice about the backup thing. Now about your answers:

Should I ask why you are not recommending ddrescue, as from what I'm reading seems to be pretty harmless?

I have already used the testdisk tool with no avail. I was able to see with that the ntfs partion that already existed when I bought the disk, so I do not think that this is an option. Also the photorec tool that testdisk comprised won't do the work as the types of files I have are not in the list of photorec.

I was really going to use gddrescue, as I saw that it is by far the best tool. I'll try to have some backup first since you mention that recovery process might fail with even more data loss.

Regards!

---

### Post by mechro on 2010-02-08
ddrescue is probably perfectly fine... I just have no experience of it.

Testdisk takes some getting used to so just in case you've missed some of its capabilities here's a link that might help...

[http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/](http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/)

---

### Post by Claus7 on 2010-02-08
Hello,

thanks very much for the comprehensive link! While searching I came across this [thread]("http://ubuntuforums.org/showthread.php?t=861763") that covers many things that are relevant to my issue.

Rule no1, have backups to more that one places and before the recovery process have a backup as well. I'll keep a backup of my intact hdd and see what I will get next.

Regards!

---

### Post by Claus7 on 2010-02-09
Just some steps:

458,1GB with left right click
539GB   with df -h

the available space:
278GB both in the window panel and from df -h


....

---

### Post by mechro on 2010-02-09
> **Claus7 said:**
> Just some steps:

458,1GB with left right click
539GB   with df -h

the available space:
278GB both in the window panel and from df -h


....

I too have such discrepancies... I think it's normal as different commands/programs use different criteria and calculation methods for usage figures.

Perhaps somebody can give you a definitive answer on the command which gives the "correct" usage but personally I wouldn't worry too much about it.

Certainly try and find old stuff that shouldn't be there but I don't think you'll get a completely "clean" system.

---

### Post by Claus7 on 2010-02-09
Hello,

thanks for the interest...

Just to mention that it is 593 so the difference is:
593-458=135GB!!! which I think that is normal to the files I'm missing. More or less I would count them around 100GB.

Still searching though,
Regards!

PS: The testdisk utility does not allow me the undelete option...

edit: From what I can get I suppose that the pointers of this folder somehow are damaged, yet I do not know a way on how to recover them...

---

### Post by Claus7 on 2010-02-09
Hello,

**this is a parenthesis** to the problem above as it will deal with a different problem, yet I think suitable to post it here, as it is a small part of the whole process:

brand new hdd 1 terabyte of storage. The first format I think that it gave 881 GB free.
The second format 877 and the last 870.

The reason for all these formats was some trials with dd_rescue and the like that resulted in a hdd with capacity of more than 4TB. Also, doing some of these attempts I came across the message:
```
Warning: Bad starting head (CHS and LBA don't match)
``` while using testdisk.

Also while using fdisk to reformat it, I was promted to choose for 2nd cylinder and on, and if choosing the 1st one the message: out of range was appearing.

So I opened gparted and I THINK that I chose Device->Choose Partition table... Doing so the result was and unallocated message and gparted became grey (I know not the best description, yet I'm trying lots of things simultaneously, I'm referring to the orthogonal area above the line /dev/sdx... which shows the capacity of the disk and how much is occupied).

Then I closed gparted and formated the disk anew with the fdisk command. The problematic message did not appear and I was able to use the 1st cylinder as the first one of my new partition. 

**parenthesis closed**

Regards!

---

### Post by Claus7 on 2010-02-09
Hello,

_backing up the old hdd_

In order to do so I tried many different tools, yet to no avail. This is how it went:

i) ```
sudo dd if=/dev/sd*input* of=/dev/sd*output*/backup-maxt1.img
```

the result was:
> dd: opening `/dev/sdoutput/backup-maxt1.img': Not a directory

So I realized that it was not possible to try this command at least in ubuntu to save an entire partition. The commands dd_rescue or ddrescue did not alter the situation. Trying this either as root or not the result was the same. Somewhere I found that these tools are suitable for files not folders, yet they are suitable for entire partitions as well...

ii) ```
cd /dev/sdinput 
cp -ax ./ /media/sdoutput/
```

the result I got was:
> cp: preserving times for `/media/sdoutput/./lost+found': Operation not permitted

so I did:
```
cd /dev/sdinput 
sudo cp -avx ./ /media/sdoutput/
```

and now I got (after some files where transfered):
> cp: cannot stat `./*some_file*': Input/output error
_____________________________________________________________________
edit3: This happened because the disk seems to be unmounted for some reason, while executing this command. Also it disappears from Places in contrast with the other disk, which if unmounted, it remains in places with the option of mounting it back.
----------------------------------------------------------------

And this is the step where the net proposes to use **e2fsck**, yet there is an urge of backing up data beforehand, so I guess is a catch 22 story. 

From what I can get, there are two copy processes: the one which copies what it sees without so much detail and the other which copies bit by bit everything (still trying to understand the difference). I'll try the simple cp -r and see what I can get. Yet, it is clear from this that the hdd is somehow corrupted.

edit1: cp -r is giving the same message
edit2: nice [link]("http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html") for e2fsck

Regards!

---

### Post by Claus7 on 2010-02-10
Hello,

the story goes on...

Almost ready to use e2fsck, I said to myself why not using once more the testdisk utility?

The reason I did that was because I changed the Label of this hdd. Why? 
While searching in the net, I discovered that with gparted someone could easily change the Label of a hdd, which means the name that the disk will have under /media/name_of_disk and on Desktop when mounted. So I decided to get rid of the common disk name and put one of myself. This would easily distinguish the two similar 1TB drives. Sorry for the missing story, yet somehow I managed to change the label of the disk with a name that was full of characters and numbers (maybe a default number was assigned to my disk). This was not a huge problem, yet I was not able to mount both of the disks simultaneously such as I was not able to mount the old hdd after the new one. Here I did not use any command line, only graphical environment. 
So, I wanted to be able to mount both drives, without taking care of which one to mount first. The odd and very big label of the drive seemed an impediment to me, as a result I decided to give a normal name back again. The message from gparted, that the change of Label might cause loss of data, did not cause any problems and very quickly the altering took place.

Having a descent label name and being able to mount both disks irrespective of the plugging order, I thought that I had made an improvement to the recovery of my disk. Also, I was curious why I was not able to see the Undeleted option of the fdisk command while choosing the option Advanced. In a windows box I was able to see some of the deleted files, so why not being able to do so in Linux?

The thing is that no undeleted files were found...

Regards!

---

### Post by Claus7 on 2010-02-10
Hello,

so I decided to use: e2fsck
```
sudo umount /media/name_of_old_disk/
sudo e2fsck -f /dev/sdb# (where # partition number)
```

doing so I waited a little and the message:
> e2fsck 1.41.9 (22-Aug-2009)
Pass 1: Checking inodes, blocks, and sizes
Inode 11681796 has illegal block(s).  Clear<y>?

I'm not sure whether I have to type yes or no in fear of destroying some of my data...

Regards!

---

### Post by Claus7 on 2010-02-14
Dear all,

here I'll give you all my experience to the issue, as now I can definitely say that even not entirely solved, at least I'm able to say that it is solved partially.

Problem (as I think it started to be): I had the problem this guy [here]("http://ubuntuforums.org/showthread.php?t=893116&highlight=noleaf") was facing, yet this was not in /proc directory, but to a folder in my external hdd.

Since I have read that I can ignore safely this error either by issuing the command find with or without the noleaf option, I did not try to do any repairing on my hdd.

Some weeks ago I decided to go to that directory and remove the files or the file (I do not remember exactly) that was causing the error.

Doing so, I got a weird message. I unplugged my drive and did not pay any more attention.

Replugging it back again I continued my every day work by adding or erasing data from the drive without any problem at all, when suddenly I decided to see some of my "older" folders content. To my surprise out of 30 or so folders, 3 of them were wiped out entirely (here we need more info):
when the hdd was mounted I was able to see 30 or so folders. From these 3 of them where there, yet all their content was missing! 

I do not know whether my effort to wipe out the faulty file or not caused the problem. I have no idea. There was more than 20 days in between and the message that I got was similar to that when I was trying the find command so I did not pay so much attention. For sure there was no mention about the folders I was missing and no connection with them. 

As a result I suppose that my action to remove the file in question created a linking error that caused content of other folders not to be seen! Being there, yet not allowing physical access to them.

The steps I followed more or less they are covered in this thread. Here I'll cover the last steps I tool in order to be able to recover at least some of my data.

I tried the command (reading [one]("http://members.iinet.net.au/~herman546/p10.html") of Herman's always reliable guides):
```
sudo e2fsck -y -f -v /dev/sd#partition
```
while the disk was **unmounted**.

with -v :verbose
-f : force
-y : do not ask every time for affirmative answer, let it be yes for all the questions (and you will need something like that or you will type yes for ages while waiting some times for very long time).

The whole command took around two days to finish to a computer more or less 5 years old, 2.5Ghz or so with double threading technology.

The result was in the lost+found foder to recover most of the data that were missing (I still have not made a full test). If you open that folder you will see many subfolders with numbers. Inside them I have seen my files intact and in some cases subfolders with their names intact as well.

Hope this is going to help someone who might face similar problems. 

**SOMETHING IMPORTANT: ** The recovered files do not seem to be deleted ones. I cannot be 100% sure, yet I do not remember going at random and erasing the content of my folders. I do not deny that this might have happened accidentally, yet in combination with an error (power failure, not proper shutdown, faulty disk...).
So about the title of the thread I think better it fits the title: recover from external usb ext3 hdd **corrupted** files and folders.

One of the errors the aforementioned command fixed as well was:
multiply-claimed blocks error  
while I did not get any error about superblocks.

Hope this cleared a little some things,
Regards!

---

### Post by Claus7 on 2010-02-27
Hello,

knowing, or better experiencing how is one to loose one's data, I'll fill in this "road to recovery" with some more info.

The data which are recovered sometimes are not easily transfered to another disk. So you have to manually create to the new disk a folder and then select the content of the old hard disk and transfer it to the new one. Also, while doing so you might face copy paste problems of some (minor) files that seem totally corrupted which hinder the transfer process. 

And something else. As soon as you recover your files take your time to copy them. Also copy the files that seem to be intact, cause the next time you plug your disk back you might face some surprises.

Story ends here I guess.

Regards!

---

