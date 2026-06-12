---
title: "dev/sda1 disk full  100% usage"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by oehq on 2009-03-30
Hello my dev/sda1 is full and no new updates will download.
I am running ubuntu 8.04 the device is 165gig.

I am sure that there are some large files that are taking up space that can be easily be deleted but I do not know how to find and delete them. 

I used kdiskfree to see that the drive is full yet I cannot drill down to the file level.  the Open is file manager does not respond. 

I tried to see the list of files with sizes in the terminal windows but the list does not show sizes (like in the DOS world)

Is there a command that will list the files with sizes like you can do in DOS?

I am sure that the problem is a few large files.... and My guess is that they are backup files from simple backup program.

this should be a very easy fix but I have spent many hours on the HOW To, cannot find a solution.

PS can you recommend a good file manager that would allow me tha ability to manage all the devices on this machine? I like Directory Opus in the windows world?

Please Help

Jim

---

### Post by kpatz on 2009-03-30
Type **mount** from a terminal and post what you get.  Then we can see what partitions you have, their sizes and mount points, and which one(s) are full.

To get file sizes, use **ls -l** (those are lowercase "L"s, not the number one).

Try **sudo apt-get clean** and see if that helps.

What backup program do you use?  Try looking in **/var/backup** or **/var/backups** and see if anything lurks there.

---

### Post by hyper_ch on 2009-03-30
also run

```

cd /
sudo du --max-depth=3 > output.txt

```

that will provide you with a text file and the filesize of each directory for 3 directory levels. You can then load that into calc for example and sort it according to dir size.

---

### Post by oehq on 2009-03-30
*********** MOUNT Results ************************* 

ls01@ls01-Dserver:/dev$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/raid5 type ext3 (rw)
/dev/sdc1 on /media/usb_drive type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
ls01@ls01-Dserver:/dev$ 

************ Mount Results **********************

I tried the 
sudo du --max-depth=3 > output.txt
appears to tke forever ???

no output  from above command

thanks 

Jim

---

### Post by kpatz on 2009-03-30
Ok, sda1 is your root file system (and your only, other than external drives).  So the problem could be anywhere from / on down.

The du command will take a while to run.  However, if the filesystem is full, it will probably fail to write the output.txt.  Try this instead:```

cd /
sudo du --max-depth=3 > /tmp/output.txt

```
It will grind for a while, and seemingly produce no output, but you'll get a file called /tmp/output.txt that you can view/sort by size to see where most of your space is being used.

---

### Post by oehq on 2009-03-30
here are the results of the first du
I then did a edit of the file for these results

is the problem in the boot?

****************** output2.txt ************

216     ./boot/grub
71068   ./boot
4       ./usr/X11R6
2320    ./usr/games
132     ./usr/share/gnome-2.0
1468    ./usr/share/foo2qpdl
96      ./usr/share/acpi-support
9560    ./usr/share/java
8       ./usr/share/console-tools
44      ./usr/share/w3m
168     ./usr/share/defoma
16      ./usr/share/firefox
88      ./usr/share/applnk
760     ./usr/share/rhythmbox
344     ./usr/share/alsa
12      ./usr/share/vte
228     ./usr/share/gnome-nettool
52      ./usr/share/launchpad-integration
4408    ./usr/share/X11
12      ./usr/share/dictionaries-common
84      ./usr/share/gstreamer-properties
16      ./usr/share/pmi
21400   ./usr/share/app-install
10848   ./usr/share/pyshared
172     ./usr/share/initramfs-tools
124     ./usr/share/evolution-data-server-2.22
2260    ./usr/share/gapi-2.0
168     ./usr/share/ggz
16      ./usr/share/keyrings
12      ./usr/share/brltty
276     ./usr/share/sbackup
1260    ./usr/share/pycentral
1440    ./usr/share/aptitude
1088    ./usr/share/xine
1464    ./usr/share/guile
60      ./usr/share/avahi
"output2.txt" 2350L, 50696C

---

### Post by philinux on 2009-03-30
I'd start with /boot. Have a browse with nautilus. Mine is 13 megabytes big with about 21 files.

[snip] No directory file size info]

---

### Post by oehq on 2009-03-30
Here is the listing for boot looks like there are img files causing the problem???
how do I delete them? is there a wild card option like 

ls01@ls01-Dserver:/boot$ rm initrd.img*
 The above command says  remove write-protected regular file 

is it ok to remove?


thanks again Jim


************************ /boot listing *****************
ls01@ls01-Dserver:/boot$ ls -l
total 70852
-rw-r--r-- 1 root root  424317 2008-02-12 04:39 abi-2.6.22-14-generic
-rw-r--r-- 1 root root  422667 2008-05-28 21:39 abi-2.6.24-18-generic
-rw-r--r-- 1 root root  422667 2008-08-20 23:46 abi-2.6.24-19-generic
-rw-r--r-- 1 root root  422781 2008-08-25 16:00 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   75311 2008-02-12 04:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root   80071 2008-05-28 21:39 config-2.6.24-18-generic
-rw-r--r-- 1 root root   80049 2008-08-20 23:46 config-2.6.24-19-generic
-rw-r--r-- 1 root root   80073 2008-08-25 16:00 config-2.6.24-21-generic
drwxr-xr-x 2 root root    4096 2008-10-24 07:17 grub
-rw-r--r-- 1 root root 7210850 2008-06-02 08:04 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root 7202340 2008-02-29 07:03 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 7429056 2008-06-04 11:26 initrd.img-2.6.24-18-generic
-rw-r--r-- 1 root root 7428767 2008-06-04 11:23 initrd.img-2.6.24-18-generic.bak
-rw-r--r-- 1 root root 7469165 2008-08-27 07:29 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root 7469188 2008-08-27 07:26 initrd.img-2.6.24-19-generic.bak
-rw-r--r-- 1 root root 7470781 2008-10-24 07:18 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7470769 2008-10-24 07:17 initrd.img-2.6.24-21-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 05:06 memtest86+.bin
-rw-r--r-- 1 root root  823535 2008-02-12 04:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root  905012 2008-05-28 21:39 System.map-2.6.24-18-generic
-rw-r--r-- 1 root root  905170 2008-08-20 23:46 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root  905365 2008-08-25 16:00 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1764536 2008-02-12 04:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root 1921528 2008-05-28 21:39 vmlinuz-2.6.24-18-generic
-rw-r--r-- 1 root root 1921464 2008-08-20 23:46 vmlinuz-2.6.24-19-generic
-rw-r--r-- 1 root root 1920376 2008-08-25 16:00 vmlinuz-2.6.24-21-generic

---

### Post by jelle_ on 2009-03-30
don't remove all versions! this will make your computer unbootable. 

you can remove all versions except the newest one (highest number). it can be done from nautilus. 
press Alt + F2 and enter gksudo nautilus /boot

---

### Post by philinux on 2009-03-30
Post the output of this

```
df -h
```

---

### Post by t0p on 2009-03-30
I wouldn't delete anything from /boot just yet!  It seems to be in line with my /boot directory.  Better check out some of the other options first.

**EDIT**: If you use the command **ls -lh** you'll get an easier to read listing (for instance file sizes in K and M).

---

### Post by philinux on 2009-03-30
Found this command will let you know the size of each directory in /


```
sudo du -sh /*
```

---

### Post by supersonicdarky on 2009-03-30
1) Why do people suggest using **du** with sudo. While there are some read-protected files, usually they are insignificatly small
2) Quite often there are a lot of packages stored if you used the pc for a while. Generally
```
sudo apt-get autoclean
```
does the job, but sometimes you need to run
```
sudo rm /var/cache/apt/archives/*.deb
```
to completely remove the cache.
3) Simplest way to get largest folders
```
du --max-depth=3 / | sort -gr | head -n 30
```

---

### Post by kanikilu on 2009-03-30
You can also use baobab or filelight to get a graphical representation of disk usage...may take some time, though.

Also, if you're really out of space, you might want to boot into the Live CD, then mount your hard-drive and use the tools (GUI or CLI) to inspect and deal with disk usage...

---

### Post by philinux on 2009-03-30
> **supersonicdarky said:**
> 1) Why do people suggest using **du** with sudo. While there are some read-protected files, usually they are insignificatly small


Because, in this case, it wont work without it. Ignore .gvfs and the other stuff and the output is very useful. 
 sudo du -sh /*
[sudo] password for xxxxx: 
7.3M	/bin
14M	/boot
0	/cdrom
580K	/dev
14M	/etc
du: cannot access `/home/philcb/.gvfs': Permission denied
18G	/home
0	/initrd.img
141M	/lib
4.5M	/lib32
0	/lib64
16K	/lost+found
8.0K	/media
4.0K	/mnt
4.0K	/opt
du: cannot access `/proc/3810/task/3810/fd/3': No such file or directory
du: cannot access `/proc/3810/task/3810/fdinfo/3': No such file or directory
du: cannot access `/proc/3810/fd/3': No such file or directory
du: cannot access `/proc/3810/fdinfo/3': No such file or directory
0	/proc
244K	/root
9.4M	/sbin
4.0K	/selinux
4.0K	/srv
0	/sys
60K	/tmp
2.4G	/usr
748M	/var
0	/vmlinuz

---

### Post by hyper_ch on 2009-03-31
and 100% usage isn't 100% usage (at least not on root) as there is space reserved so that root can still do stuff.

---

### Post by kpatz on 2009-03-31
That size (70+ megs) for /boot is normal on Hardy.

If you still have that output.txt file sitting in /tmp, issue this command:

```
sort -nr /tmp/output.txt | head -20
```

This will give you the top 20 (largest) directories.

Also, do **du --max-depth=3 -h /home**.  You might have a lot of stuff in /home eating up space which could be cleaned up.

---

### Post by PukingPenguin on 2009-03-31
Is it just me, or does it seem a little unlikely that a 165GB disk is actually full?
And if it is, just rm a movie or two...'cause you sure as he11 didn't fill that much space up with text files.

---

### Post by philinux on 2009-03-31
> **PukingPenguin said:**
> Is it just me, or does it seem a little unlikely that a 165GB disk is actually full?
And if it is, just rm a movie or two...'cause you sure as he11 didn't fill that much space up with text files.

Depends how he partitioned his disk. If he only allocated say 4gig for root it could have become full.

---

### Post by PukingPenguin on 2009-03-31
> **philinux said:**
> Depends how he partitioned his disk. If he only allocated say 4gig for root it could have become full.

Right, that's sort of what I was getting to. Why don't we have a look at that? ```
sudo fdisk -l
```

---

### Post by mikechant on 2009-03-31
> Depends how he partitioned his disk.

Yes, this is quite likely to be at least partly a partition size issue.

oehq, could you cut and paste the output from the command

fdisk -l

(that's letter l not number 1)
 
This will show how much space you've allocated to your partitions and how full each one is.

---

### Post by kpatz on 2009-03-31
> **mikechant said:**
> Yes, this is quite likely to be at least partly a partition size issue.

oehq, could you cut and paste the output from the command

fdisk -l

(that's letter l not number 1)
 
This will show how much space you've allocated to your partitions and how full each one is.fdisk -l will show partition sizes, but not how full each one is.

Use the command **df -h** to get sizes and USAGE of your partitions.

---

### Post by hyper_ch on 2009-03-31
> **PukingPenguin said:**
> Is it just me, or does it seem a little unlikely that a 165GB disk is actually full?
And if it is, just rm a movie or two...'cause you sure as he11 didn't fill that much space up with text files.

I've seen it often enough that moving stuff to root trash or backing up to a wrong folder fills harddrive quite quickly.

---

### Post by oehq on 2009-03-31
I cleared the files in /backup and /backups
but I hav not been able to find the directory that is so full???
/dev/sdb1 still shows full.

any other ideas?



here is the   ls01@ls01-Dserver:/var/backups$ df -h

******************** df -h report ********************
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             141G  141G     0 100% /
varrun                1.5G  260K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   60K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1             584G  243G  311G  44% /media/raid5
/dev/sdc1             932G  687G  246G  74% /media/usb_drive
overflow              1.0M   52K  972K   6% /tm

---

### Post by oehq on 2009-03-31
here are the results of the 
ls01@ls01-Dserver:/$ sudo du --max-depth=3 / | sort -gr | head -n 30

Hope this helps


********** RESULTS ********************
du: cannot access `/proc/8396/task/8396/fd/3': No such file or directory
du: cannot access `/proc/8396/task/8396/fdinfo/3': No such file or directory
du: cannot access `/proc/8396/fd/3': No such file or directory
du: cannot access `/proc/8396/fdinfo/3': No such file or directory
994618843	/
972751235	/media
718200983	/media/usb_drive
254550240	/media/raid5
254550228	/media/raid5/LS01-raid_data
188898260	/media/usb_drive/GRSync Backup to USB
141110485	/media/usb_drive/2008-10-24_07.27.08.829427.ls01-Dserver.ful
94346565	/media/usb_drive/2008-08-16_20.00.18.006689.ls01-Dserver.ful
92730593	/media/usb_drive/2008-07-15_20.00.14.394526.ls01-Dserver.ful
88075109	/media/usb_drive/Keep_backups
38314229	/media/usb_drive/2008-06-12_20.00.11.754461.ls01-Dserver.ful
28054874	/media/usb_drive/2008-11-01_20.00.21.813374.ls01-Dserver.inc
20994189	/media/usb_drive/2008-05-08_20.00.06.140523.ls01-Dserver.ful
18222720	/home
18222716	/home/ls01
17974024	/home/ls01/bat
16721597	/media/usb_drive/2008-09-17_20.00.16.239127.ls01-Dserver.ful
2635528	/usr
1745122	/media/usb_drive/2008-11-07_20.00.17.168155.ls01-Dserver.inc
1713914	/media/usb_drive/2008-10-30_20.00.15.880649.ls01-Dserver.inc
1709654	/media/usb_drive/2008-11-02_20.00.19.007231.ls01-Dserver.inc
1705738	/media/usb_drive/2008-10-31_20.00.19.587962.ls01-Dserver.inc
1704555	/media/usb_drive/2008-11-08_20.00.19.419519.ls01-Dserver.inc
1375784	/usr/lib
992872	/usr/share
524940	/lib
415532	/usr/lib/kde4
413568	/var
328796	/lib/modules
297176	/usr/lib/openoffice

---

### Post by mikechant on 2009-03-31
The figures you've given don't show the relevant disc space actually being used. If we ignore the /media stuff, because this is actually on sda1 and sdc1, the only significant thing is about 20Gb for /home. So where's the other 100Gb+ gone?
A wild guess: Suppose you accidentally made some large backups to /media/usb_drive while the sdc1 drive was not connected or not mounted for some reason. This would actually use space on sdb1, which would then be hidden when the drive was next mounted.
How about disconnecting the external drive and then running the 
```
sudo du --max-depth=3 / | sort -gr | head -n 30
```
command again? Or just checking if there's anything in /media/usb_drive when sdc1 is unmounted/disconnected.

I assume this could only apply to sdc1, not to sda1 since I guess sda1 is always connected and mounted (internal?)

---

### Post by RetchingRabbit on 2009-03-31
i don't know about the rest of y'all, but I still want to know how big the partitions are, be it via fdisk -l or df -h....

---

### Post by kpatz on 2009-03-31
> **RetchingRabbit said:**
> i don't know about the rest of y'all, but I still want to know how big the partitions are, be it via fdisk -l or df -h....He posted that a few posts up...

> /dev/sdb1 141G 141G 0 100% /
varrun 1.5G 260K 1.5G 1% /var/run
varlock 1.5G 0 1.5G 0% /var/lock
udev 1.5G 60K 1.5G 1% /dev
devshm 1.5G 12K 1.5G 1% /dev/shm
lrm 1.5G 39M 1.5G 3% /lib/modules/2.6.24-21-generic/volatile
/dev/sda1 584G 243G 311G 44% /media/raid5
/dev/sdc1 932G 687G 246G 74% /media/usb_drive
overflow 1.0M 52K 972K 6% /tm...

Try this:  unmount everything on /media (/dev/sda1 and /dev/sdc1), and then run the ```
sudo du -x --max-depth=3 / | sort -gr | head -n 30
``` command again.  (Note that I added -x to the du command--this keeps you on the root filesystem, and doesn't count other filesystems like /tmp).

---

### Post by oehq on 2009-04-01
You hit the nail right on the head!!!
That was exactly what happened. I suppose there was a time where the usb_drive was not connected so the backup went to the sdb1 (root) drive and created the /media/usb_drive on the sdb1 drive. then it did the 120gig backup to the new directory with the same name as the mount piont for the usb drive. 

Just as you said this directory was not visable when the sdc1 was mounted. After unmount of both sda1 and sdc1 it was very clear where the problem was see below (RESULTS #1).

I deleted the file on sdb1 and the results #2 show a empty sdb1 with only 16% utilization.

You guys are the BEST!! ... I never would have got there without you...

THANK YOU,  THANK YOU,  THANK YOU 

Jim

**************** RESULTS #1   BEFORE with unmounted sda1 and sdc1 *************** 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             141G  141G     0 100% /
varrun                1.5G  260K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   52K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-21-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
ls01@ls01-Dserver:~$ 
ls01@ls01-Dserver:~$ sudo du -x --max-depth=3 / | sort -gr | head -n 30
147212092	/
125385532	/media
125385516	/media/usb_drive
125385512	/media/usb_drive/2008-12-01_20.00.05.392058.ls01-Dserver.ful
18222636	/home
18222632	/home/ls01
17974024	/home/ls01/bat
2635528	/usr
1375784	/usr/lib
992872	/usr/share
485160	/lib
415532	/usr/lib/kde4
412516	/var
297176	/usr/lib/openoffice
289016	/lib/modules
207748	/var/lib
179148	/usr/share/gnome
155992	/lib/linux-restricted-modules
133844	/var/tmp
133328	/usr/src
107468	/usr/bin
101624	/usr/share/doc
100348	/home/ls01/Desktop
100260	/usr/share/fonts
85704	/usr/share/icons
84028	/home/ls01/.mozilla
74008	/lib/modules/2.6.24-18-generic
73248	/lib/modules/2.6.24-21-generic
72808	/lib/modules/2.6.24-19-generic
68948	/lib/modules/2.6.22-14-generic
ls01@ls01-Dserver:~$ 

 ************************** Fixed RESULTS after delete *******************

ls01@ls01-Dserver:~$ sudo df -h
[sudo] password for ls01: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             141G   21G  113G  16% /
varrun                1.5G  260K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   52K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-21-generic/volatile
overflow              1.0M   52K  972K   6% /tmp
/dev/sda1             584G  244G  311G  44% /media/raid5

---

### Post by ASL4U on 2009-04-05
Can you tell me how you did this please?
I am a new user. I did something (I dont know what) but it now makes my / show full no matter how much data I take out of it. 
I cannot save text files - so I cannot run the reports that have been recommended here -
I have tried to unmount sda1 but it says the device is busy and wont let me.
I have removed every file on my root - the free space on root is growing - but it is still reported as full.

any help?
Thanks

---

