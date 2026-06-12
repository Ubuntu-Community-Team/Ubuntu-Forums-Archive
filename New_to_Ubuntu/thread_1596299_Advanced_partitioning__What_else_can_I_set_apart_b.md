---
title: "Advanced partitioning:  What else can I set apart besides /home?"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by diablo75 on 2010-10-14
I love the setup I have on my system because I use a separate partition for /home and one for root.  But I've noticed during manual partitioning in the past that you could actually create pretty much as many partitions as you want and could assign even more folders, not just /home, to have its own partition.  I was wondering what folders I might try to give a partition in addition to /home and what advantages I would get for each folder.

---

### Post by sikander3786 on 2010-10-14
This page pretty much lists the information you need. (if you didn't see it already)

[https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html](https://help.ubuntu.com/10.04/installation-guide/i386/apcs03.html)

---

### Post by indytim on 2010-10-14
Assuming that you have the real estate (available space on your hard drive), it really depends on where your interest and needs reside.  As a thought starter, I have separate partitions for:
[LIST]
Digital photographs in process
Finished digital photographs
Digital Music
Image Backups for my primary operating system hard drive
Image Backups for my data partitions
Video Projects
Documents
[/LIST]

Within each of these partitions I usually have a number of directories (folders).

You get the idea.  Hope this also helps.

IndyTim / DataMan

---

### Post by SeijiSensei on 2010-10-14
On servers, I generally allocate a separate partition to /var, which gets a lot of reads and writes if the machine is running a web or mail server.  I also allocate a separate partition to /tmp and mark it noexec to prevent someone exploiting an unpatched hole in a server daemon I'm running by dropping a script into /tmp and running it from there. (Had that happen once years ago with Apache 1.1.)

On my desktop, I have a separate /home partition, one for /usr/local, and another where I can put distributions I'm testing.  Maintaining a separate /usr/local partition is useful only if you compile software from source.  By default most applications built from source install themselves under the /usr/local tree.  By making it a separate partition I can see those applications from both my current distribution and any other one I'm testing in the extra partition.  Having a separate /home partition makes it available to the testing distribution as well.

---

### Post by Megaptera on 2010-10-14
A useful guide (with screenshots) for a simple set up (separate home and swap shown)

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

---

### Post by srs5694 on 2010-10-14
I wrote [this article](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) on this topic a while ago.

Personally, I wouldn't create separate partitions for different types of user data, as indytim suggests, without some compelling reason (such as a need imposed by having multiple physical hard disks). The problem is that personal storage needs tend to shift frequently, in my experience, and creating separate partitions makes it difficult and dangerous to change how much space is allocated to one purpose vs. another. This same drawback applies to splitting off different system partitions (/var, /usr, and so on), but their needs tend to be significantly more stable over time, vs. my personal needs for music, photos, and so on.

---

### Post by pricetech on 2010-10-14
Links from above posts give you pretty much the technical aspects, but it really depends upon what you're doing, or planning to do, with your computer.

As an example, I considered a separate partition for /var/spool/apt-mirror on my local mirror and probably will do that next time.  That puts my mirror on a separate partition which can more easily be migrated to a new system should I need to retain the old mirror.

I also keep a repository for windows software, which again can be put on a separate partition for easier migration.

Just a couple of examples that might help answer your question or provoke thought.

---

### Post by diablo75 on 2010-10-14
Well here's what I was hoping for...

In the past, when I've had system failures that I didn't want to take the time and energy to investigate, I would just reinstall the OS by formatting / and setting the /home partition to be the new home (without formatting it of course) for the fresh install.  This is great because a lot of personal preferences for things like Firefox/Mozilla, Evolution, Gnome, and who knows what else are just there, right away.

But what's not there are programs I may have installed before erasing the /.  Now it's obvious that they would be eliminated if I didn't have any other partitions except for / and /home, so I was wondering if there was a way to preserve installed programs (like Virtualbox) in addition to things in the home folder.  Is that possible?

---

### Post by srs5694 on 2010-10-14
It's very very impractical, and perhaps impossible, if the programs are installed via Debian packages, as is the case for most programs you'll install in Ubuntu. This is because most packages install most or all of their files in multiple standard directories, such as /usr/bin, /usr/lib, and so on. Each of these directories ends up holding files from hundreds of different packages, and there's no practical way to isolate a few packages' files on a separate partition. There's also the issue of the database of installed files, which wouldn't reflect the packages you've preserved, if you could do that at all.

That said, locally-compiled programs normally go in /usr/local, so if you just wanted to carry over a small number of programs that you manage yourself, you could do so by putting /usr/local on its own partition and installing those programs by downloading the source code and installing them manually. You'd then have to manage updates in the same way. Normally, this isn't a viable option for more than a very small number of programs, and usually it's reserved for programs that are very obscure (and so that aren't available via APT) or that you want to customize or optimize in some way.

Some commercial programs install in /opt, which you can manage much like /usr/local, so similar comments apply to /opt as to /usr/local.

You can preserve virtualization environments by putting them in their own directory and making that a separate partition. The software you run to launch a virtual environment, though, is a regular Ubuntu program and so will be managed as such (or it could be locally compiled or stored in /opt; I don't know the status of VirtualBox specifically on this score).

---

### Post by oldfred on 2010-10-14
You can easily back up a list of the standard installed programs and use that to reinstall. I added this command to the rsync back up that I run so it has an updated list of applications on every backup. If you have any custom system settings in /etc you might want to back those up also.

 dpkg --get-selections > ubuntu-files

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by xyepblra on 2011-01-04
> **oldfred said:**
> I added this command to the rsync back up that I run so it has an updated list of applications on every backup.
This is a brilliant idea! Oldfred, do you think you could share your rsync config file?

---

### Post by psusi on 2011-01-04
You can split off whatever directories you want, but there is no advantage to doing so.  The disadvantage of course, is that you can fill one up while still having room on another and you're out of luck.

The only reason to even have a separate /home is if you want to share the same home partition between multiple Linux installs.

---

### Post by oldfred on 2011-01-04
My backup is just this with my paths, the above dpkg list of installed apps and I plan to add a run of bootinfo script so I have a current copy of my system config with all the partition details etc. I have saved many copies of results.txt as I run it before & after every system change.

Quote:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh

-l: copies symlinks as symlinks
-t: preserves modification times
-D: preserves device and special files


#!/bin/bash
# backup script
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
echo "starting..."
cp /etc/apt/sources.list ~/Documents/LinuxDocs/CurrentSys/sources.list.backup
dpkg --get-selections > ~/Documents/LinuxDocs/CurrentSys/ubuntu-files

rsync -aruvP /mnt/data_DT/Documents /usr/local/fred/data/

#rsync -auvP /home /media/backup
#rsync -auvP /share /media/backup
#rsync -auvP /media/floppy /media/backup
#rsync -auvP /etc /media/backup
echo "done"
exit 0

make it executable
chmod +x mybackup.sh

run it
./mybackup.sh

of course, do the dry run first as I said before
thank you very much. I made a symbolic link from /bin/backup to /root/backup.sh, thanks!!!!!

---

### Post by srs5694 on 2011-01-05
> **psusi said:**
> You can split off whatever directories you want, but there is no advantage to doing so.  The disadvantage of course, is that you can fill one up while still having room on another and you're out of luck.

The only reason to even have a separate /home is if you want to share the same home partition between multiple Linux installs.

I disagree. Strongly. A separate /home partition has the very real advantage that your user data remain safe if/when you need to completely wipe and re-install the OS. There are a number of other minor advantages, as well as advantages to splitting off other directories into their own partitions; however, most of these are rather specialized advantages and don't apply to the average Ubuntu user. Still, I wouldn't dismiss them as completely as you have. If you care to learn more, there are lots of Web sites on the subject. I wrote [an article on the topic for IBM developerWorks](http://www.ibm.com/developerworks/aix/library/au-unixfilesys/index.html) a couple of years ago.

---

### Post by psusi on 2011-01-05
> **srs5694 said:**
> I disagree. Strongly. A separate /home partition has the very real advantage that your user data remain safe if/when you need to completely wipe and re-install the OS. 

You can reinstall just fine and leave your home directory intact; just don't check the format box.

> **srs5694 said:**
> There are a number of other minor advantages, as well as advantages to splitting off other directories into their own partitions; however, most of these are rather specialized advantages and don't apply to the average Ubuntu user. Still, I wouldn't dismiss them as completely as you have. If you care to learn more, there are lots of Web sites on the subject.

Such as?

Back in the 90s it might have made sense for servers with multiple disks because it meant the lengthy fsck after a crash could be done in parallel and faster, and maybe your mail spool directory could see some gains being on a different filesystem optimized for that purpose, and your /boot fs could be unmounted and kept safe, but these days your average desktop user with a single disk gains nothing from partitioning it into multiple filesystems other than the ease of sharing one between multiple operating systems.

---

### Post by srs5694 on 2011-01-05
> **psusi said:**
> You can reinstall just fine and leave your home directory intact; just don't check the format box.

I wouldn't trust that to work correctly if the system is totally messed up. Furthermore, it won't work at all if you want to switch to a different distribution, change filesystems on the boot partition, etc.

(re: Web sites on the subject of partition allocation.)

> Such as?

I posted a link to one I wrote. You can do a Web search to find others; I don't happen to have a bunch bookmarked. Also, search on "Linux FHS," since the FHS is relevant to this discussion, although it's more about the layout of directories than about partitions per se.

> Back in the 90s it might have made sense for servers with multiple disks because it meant the lengthy fsck after a crash could be done in parallel and faster, and maybe your mail spool directory could see some gains being on a different filesystem optimized for that purpose, and your /boot fs could be unmounted and kept safe, but these days your average desktop user with a single disk gains nothing from partitioning it into multiple filesystems other than the ease of sharing one between multiple operating systems.

I did state that the advantages of separating most non-/home directories onto their own partitions are rather limited for the average Ubuntu user. What I object to is the absolute nature of your statements, like "there is no advantage" to splitting off separate partitions. *Sometimes* there are advantages, and saying there *never* are is inaccurate, or at best imprecise.

---

### Post by iconoclast hero on 2011-05-26
I don't want to wade into the argument about whether or not it is wise to partition, but I just dumped the Natty partition that I had and I'm trying to optimize my /home partition.  For some reason, I have a separate partition for /usr/local.  I am fairly certain that I didn't put it there and /etc/fstab says of it 
```
# /usr/local was on /dev/sda6 during installation
```I was thinking I might be able to use that for both /home and /usr/local but I'm finding that is probably not going to work.  That said, I have no idea where it came from and I rarely compile from source (I think I've done it twice or three times, with great difficulty, and with ruby scripts).  Would it make sense just to reformat it to ext4 (as it is now) to remove the /usr/local data and then to copy my /home info to that and call it a day?  The partition is just about 21 GiB according to gparted.

```
Disk /dev/sda: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d64e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       54262   435853953   83  Linux
/dev/sda2           54262       60802    52531201    5  Extended
/dev/sda5           60667       60802     1079296   83  Linux
/dev/sda6           57634       58048     3333456   82  Linux swap / Solaris

Partition table entries are not in disk order

```

(There are also 25 GiB unallocated that are going back to /dev/sda1 as soon as I get around to booting from disc).

---

### Post by iconoclast hero on 2011-06-10
bump?

---

### Post by psusi on 2011-06-10
Please start your own thread instead of trying to hijack this one.

---

### Post by iconoclast hero on 2011-06-10
Sure, just that it seemed to be on topic since I was wondering what else  besides /home should be partitioned, why it did it automatically  install /usr/local/ and what is it for...

---

