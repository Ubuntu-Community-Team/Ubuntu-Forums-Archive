---
title: "Hard disk suddenly full"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by jimsheep on 2009-08-25
hi all

so i came home from work this morning and couldn't download my email...not enough disk space.  so i deleted a whole bunch of email. did apt-get clean, autoclean, and autoremove and made sure the trash was empty.  still too much disk space used!  i know i run it a little close to full, but i also know how much i should have,  so, here's the output from df -h:

```

jimsheep@jimsheep-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  8.2G  770M  92% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  372K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.9M 1010M   1% /dev
tmpfs                1013M  288K 1012M   1% /dev/shm
lrm                  1013M  2.2M 1010M   1% /lib/modules/2.6.27-14-server/volatile
/dev/sda6              64G   56G  7.9G  88% /media/super
/dev/sdb5             5.8G   15M  5.8G   1% /media/EXTRAS
/dev/sdb1             135G  126G  3.6G  98% /media/disk

```

i should have more than 770MB in /! i tried to empty root's trash, but got:

[quote="The folder contents could not be displayed."]Sorry, could not display all the contents of "trash": Operation not supported[/quote]

WTFH!?:confused:

i can't remember anything else i should do...

---

### Post by click4851 on 2009-08-25
maybe check your log files, make sure nothing sketchy happened....heck make sure the log files didn't fill up and overwhelm your /.

---

### Post by jimsheep on 2009-08-25
> **click4851 said:**
> maybe check your log files, make sure nothing sketchy happened....heck make sure the log files didn't fill up and overwhelm your /.
/var/log is only 11MB, and i'm not sure what to look for in the log files.

---

### Post by inobe on 2009-08-25
check this out jim, just gave advice for full root partition here

[http://ubuntuforums.org/showthread.php?p=7847199#post7847199](http://ubuntuforums.org/showthread.php?p=7847199#post7847199)

---

### Post by jimsheep on 2009-08-25
fdisk -l:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000902fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246        9729    68147730    5  Extended
/dev/sda5            1246        1494     2000061   82  Linux swap / Solaris
/dev/sda6            1495        9729    66147606    b  W95 FAT32

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde1540d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       17793   142922241   83  Linux
/dev/sdb2   *       17794       19173    11084850    7  HPFS/NTFS
/dev/sdb3           19174       19929     6072570    5  Extended
/dev/sdb5           19174       19929     6072538+   b  W95 FAT32

```
and searching just found the large media files in /dev/sdb1 and /dev/sda6.  OS is on /dev/sda1, winxp on /dev/sdb2

---

### Post by inobe on 2009-08-25
filelight is a decent gui app that will help you find files to remove.

don't install it now, use it when you clean up to monitor what gets full.

you could adjust the size in last command to search for smaller files.

---

### Post by mapes12 on 2009-08-26
This worked for me: [http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by jimsheep on 2009-08-26
ok, am working through the second link posted.  i have a limited amount of time at home, so i apologise for the delay in responses.

oh, and i'll get fired if i ssh into my home box.

---

### Post by drs305 on 2009-08-26
FYI, I wrote a follow-on to the link mapes12 posted concerning Trash. I expanded it it include troubleshooting for a variety of things that can cause a disk to fill up.

The expanded post is available by clicking the "Disk Space" link in my signature line (the wiki), or [here]("http://ubuntuforums.org/showthread.php?t=1122670") (the post the wiki was based on).

---

### Post by Seine on 2009-08-26
The following will display the size of the files and directories at the current path (including all nested files and directories). ```
du --max-depth=1 | sort -nr
```
It can take some time to run. Keep delving into the biggest directory until you find the culprit.


Or just run Application | Accessories | Disk Usage Analyser.

---

### Post by jimsheep on 2009-08-27
> **drs305 said:**
> FYI, I wrote a follow-on to the link mapes12 posted concerning Trash. I expanded it it include troubleshooting for a variety of things that can cause a disk to fill up.

The expanded post is available by clicking the "Disk Space" link in my signature line (the wiki), or [here]("http://ubuntuforums.org/showthread.php?t=1122670") (the post the wiki was based on).
i ran through some of the space-freeing steps outlined in the link in your sig...got /dev/sda1 up to 880MB free, but that still seems a little low.  granted, 1GB of the 9.4GB disk is pictures.

can i safely remove some of the folders that appear under /lib/modules?  exempli grata: /lib/modules/2.6.27-11-generic, if i'm using kernel 2.6.27-14-generic?

---

### Post by Baelus on 2009-08-27
Do you have any drives set in fstab that auto mount on a directory in /?

I think if the drive failed to mount and files were copied to the directory, then the drive was mounted later, the copied files that are "underneath" the mounted drive will be hidden.

---

### Post by candtalan on 2009-08-27
I had this *sudden* problem - it was because I had a backup program and on one occasion the target drive was not connected nor mounted, and the backup simply continued and created a new folder on my data drive and put the backup into that, in this case totally filling it up.

Are you using a backup program of any sort?

---

### Post by jimsheep on 2009-08-27
no backups, and the only things that mount automatically are / and a second partition that i use as a go-between for windows and ubuntu.  windows is on a different physical drive than ubuntu.  i checked /media/* for files that shouldn't be there (with everything unmounted, of course) and there's nothing there, even using gksudo nautilus.

---

### Post by drs305 on 2009-08-27
Jim,

If you still haven't found the problem and would like us to take a look, run these commands and post the results of the second one. Close all your open apps. The first command will try to unmount all your partitions. It will say "busy" but should leave only your system partition mounted. Then run and post the results of the second command.
```

sudo umount -a
sudo du -h --max-depth=1 / | sort -nr

```

We can compare your results with ours and perhaps see where the disk usage is out of the normal range.

---

### Post by jimsheep on 2009-08-27
ok; i'll post it sometime after 5.30pm MDT.  thanks for all the help so far!

---

### Post by jimsheep on 2009-08-27
```
jimsheep@jimsheep-desktop:~$ sudo du -h --max-depth=1 / | sort -nr
du: cannot access `/proc/6673/task/6673/fd/3': No such file or directory
du: cannot access `/proc/6673/task/6673/fdinfo/3': No such file or directory
du: cannot access `/proc/6673/fd/3': No such file or directory
du: cannot access `/proc/6673/fdinfo/3': No such file or directory
813M	/lib
355M	/var
132K	/tmp
105M	/boot
76M	/opt
25M	/root
18M	/etc
16K	/media
16K	/lost+found
8.4M	/sbin
8.0K	/Shane
8.0G	/
6.1M	/bin
4.5G	/usr
4.0K	/srv
4.0K	/mnt
3.2M	/dev
2.2G	/home
0	/sys
0	/proc

```
and half of /home is .jpg files.

---

### Post by drs305 on 2009-08-27
Nothing looks way out of line. Your /usr folder is about 2GB larger than mine but I have almost nothing in /usr/src and have removed the default games.

I reread the entire thread. Of course, 8GB isn't a large partition for Ubuntu anyway, since you are storing stuff in your /home folder. I see you don't have lots of room in sda5 or sda6 either, but 2GB of extra space in your Ubuntu partition would give you a bit of breathing room.

Were you ever able to get rid of/empty the Trash folder in /root/.local/share?

---

### Post by jimsheep on 2009-08-27
yes, i was able to find and delete it...and it stayed deleted, so far.

i also notice i'm back down to 780MB from 880MB, and i haven't changed anything.  it's not my email, 'cause i just deleted it and it didn't change.

---

### Post by rbp on 2009-08-28
same thing happened to me - came home and suddenly 20 GB had disappeared. I upgraded my kernel, reboot, and the space was back.

---

