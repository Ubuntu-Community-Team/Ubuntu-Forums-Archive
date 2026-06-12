---
title: "ext3 file system creation in partition #1 of SCSI1 failed."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by MacQ32 on 2009-01-05
First off, today was the first day I've messed around with linux.  I have an Inspiron 6400 and am trying to run Ubuntu 8.10 (and plan to eventually use winxp as well).

I've run into an issue partitioning my internal hard drive.  I chose to manually partition the drive as follows:

/dev/sda1 = 100GB EXT3 (/root)

/dev/sda5 = 3GB SWAP

/dev/sda6 = 17GB FAT32 (I've tried both /windows as well as setting this partition to inactive)

When "Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0)..."  I come across these two error messages:

"The NetworkManager applet could not find some required resources.  It cannot continue." 

as well as

"The ext3 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed."


Any suggestions as to how I can resolve the issue would be extremely appreciated!  Thanks

---

### Post by jrusso2 on 2009-01-05
Sounds to me like you need to redo the ext 3 partition.  What software did you use to make it?

---

### Post by MacQ32 on 2009-01-05
> **jrusso2 said:**
> Sounds to me like you need to redo the ext 3 partition.  What software did you use to make it?

Thanks for the response, I have tried to re-do the partition a number of times, right now I am in the process of auto-partitioning into one 120GB partition (just to see if it would work)... and I just received the same error message.

"The ext3 file system creation in partition #1 of failed."

I am using the "Install" wizard on the desktop.  I had downloaded the ubuntu 8.10 386i ISO off the linux website and am running off of that disc.

Hope that answers your question, if not let me know and I'll try to get you the answer you were looking for.


Appreciate the quick reply

---

### Post by Den_Citronen on 2009-01-05
Not really an solution to the problem itself, but have you tried to just start all over with the installation?

Another solution (sort of bypassing the problem) might be to delete all partitions using Gparted (System -> Administration -> Partition Editor) before you start the installer, so the disks are clean when you begin.

---

### Post by MacQ32 on 2009-01-05
Not really an solution to the problem itself, but have you tried to just start all over with the installation?

Another solution (sort of bypassing the problem) might be to delete all partitions using Gparted (System -> Administration -> Partition Editor) before you start the installer, so the disks are clean when you begin.

Thanks for chiming in Citronen.  I have tried starting the installation over at least 6 or 7 times.  Every time I get the ext3 error message ubuntu pretty much freezes up and I am forced to restart the computer and try the process over.

I used GParted and created as follows
93GB to the ext3 /
16GB to the ntfs /windows
3GB to the linux-swap

I ran into "An error has occurred while applying the operations"

When I access the "Save Details" This is what I find:


Create Primary Partition #1 (ext3, 92.77 GiB) on /dev/sda  00:02:11    ( ERROR )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 39873330
end: 234436544
size: 194563215 (92.77 GiB)
set partitiontype on /dev/sda1  00:00:00    ( SUCCESS )
     	
new partitiontype: ext3
create new ext3 filesystem  00:02:11    ( ERROR )
     	
mkfs.ext3 -L "/" /dev/sda1
     	
Filesystem label=/
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
6086656 inodes, 24320401 blocks
1216020 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
743 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872


Followed by a long list of Writing Inode Tables

then

mke2fs 1.41.3 (12-Oct-2008)
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir





edit: just saw that you suggested I delete all partitions then try install over, I'm going to do that now.  The message above is my result when I deleted and re-partitioned with gparted.

edit #2: Just deleted all partitions and tried to auto-partition into one part and received the initial ext3 error once again.

---

### Post by MacQ32 on 2009-01-05
I also just learned the SWAP partition is being rejected with the same error as well, if that makes a difference.

thanks for the help guys

---

### Post by MacQ32 on 2009-01-06
Sorry to bump, but I'm hoping I'm not the first person to run into this issue.  Has anyone else even seen this? Let alone find a solution

---

### Post by Den_Citronen on 2009-01-07
> **MacQ32 said:**
> Sorry to bump, but I'm hoping I'm not the first person to run into this issue.  Has anyone else even seen this? Let alone find a solution

Alright, digged a bit deeper into the problem. Others have similar problems.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908)

In there I found a solution which works accordingly to (permalink to reply):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/5](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/5)

And the fix is (permalink to reply):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/4](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/4)

So.. If I get it straight, I think this is how you should do:

Open up a terminal in the Live-CD environment.

```
sudo nano /lib/partman/commit.d/30parted
```

Edit the file to look like this (only diffrence is that update-dev is added):

```

#!/bin/sh

. /lib/partman/definitions.sh

disable_swap
for dev in $DEVICES/*; do
    [ -d "$dev" ] || continue
    cd $dev
    open_dialog COMMIT
    close_dialog
    update-dev
done
```

Then start the installation.

Works?

## Edit, oh... Just realized that was Kubuntu - I have no idea if it'd be the same for Ubuntu...

---

### Post by Den_Citronen on 2009-01-07
[http://whynotwiki.com/2007-07-27:_Installing_Ubuntu#Problem_2:_ext3_file_system_creation_..._failed](http://whynotwiki.com/2007-07-27:_Installing_Ubuntu#Problem_2:_ext3_file_system_creation_..._failed)

Parhaps that's something.

EDIT::
Or second reply at this one?

[http://www.linuxquestions.org/questions/linux-newbie-8/installation-of-ubuntu-8.04-fails-repeatedly-due-to-partitioning-problems-655366/](http://www.linuxquestions.org/questions/linux-newbie-8/installation-of-ubuntu-8.04-fails-repeatedly-due-to-partitioning-problems-655366/)

---

### Post by okan_trav on 2009-01-07
I just tried the first solution identified by Den_Citronen (adding update-dev) and can confirm that it solved the problem in Ubuntu.  Many, many thanks both to the original poster and Citronen.  My installation is now progressing just fine.

---

### Post by Den_Citronen on 2009-01-07
Awesome. One down, one to go!

---

### Post by liljoentx on 2009-01-31
I haven't researched all of your discussion that deeply, but I did note a similarity to the same issue, which I also have had. It is also not generic to Ubuntu but the partitioner used, plus the fact that the hard drive (I believe your's are also IDE like mine) are being recognized as being SCSI drives (sda), when they should appear as hda.

I'm waiting to hear from some folks more expert with Linux to see what is actually the problem and if they have a remedy.

Lil'Joe

---

### Post by lethalfang on 2009-02-24
I've run into pretty much the exact problem described by the original poster. 
After I tried this quoted remedy, the installation keeps going back to the Installation prompt (e.g., How do you want to partition the disk? Guided, Manual, etc.)

Anyone has any ideas how to proceed?

Thanks in advance!

Additional Info Edit:
While the installation disk is able to find my 400GB hard drive (SATA recognized as SCSI) during the installation prompt, the partition editor in LiveCD does NOT see it. Nor do I see the hard drive listed when I type in "sudo fdisk -l."

Any ideas, anyone?


> **Den_Citronen said:**
> Alright, digged a bit deeper into the problem. Others have similar problems.

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908)

In there I found a solution which works accordingly to (permalink to reply):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/5](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/5)

And the fix is (permalink to reply):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/4](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/99908/comments/4)

So.. If I get it straight, I think this is how you should do:

Open up a terminal in the Live-CD environment.

```
sudo nano /lib/partman/commit.d/30parted
```

Edit the file to look like this (only diffrence is that update-dev is added):

```

#!/bin/sh

. /lib/partman/definitions.sh

disable_swap
for dev in $DEVICES/*; do
    [ -d "$dev" ] || continue
    cd $dev
    open_dialog COMMIT
    close_dialog
    update-dev
done
```

Then start the installation.

Works?

## Edit, oh... Just realized that was Kubuntu - I have no idea if it'd be the same for Ubuntu...

---

### Post by lethalfang on 2009-02-24
^^^
Any suggestions, anyone?

---

### Post by lockettowl on 2009-04-19
I feel bad for digging up this somewhat old thread, but I've been having the same problem and have found no solutions - I've looked all over and tried everything that my non-expert skill will allow, to no avail. Neither the installer nor GParted will create a new partition. I even cleared out my old partition to try to start from scratch with clean space, and nothing. In the installer I keep getting the same error message.

There must be something that I can do. I can't just keep using only the Live CD as my only OS. Has anyone found a solution yet?

---

### Post by mikechant on 2009-04-20
You could try the gparted live CD instead of running gparted off the Ubuntu CD
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

I believe some people have success with this.

---

