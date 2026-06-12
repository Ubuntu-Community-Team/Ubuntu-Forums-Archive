---
title: "Root partition is full, how can that be?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by jlbr21 on 2009-06-16
Hi, I have been trying to install some stuff, like python scripts for Gimp, and I kept getting the message that there was no space left, then I checked and it seems like my root partition is full!

I have 9.4 gb as root partition, and I cant seem to find the file(s) that are clogging up my root partition.

Please help.

BTW, I have apt-get clean'ed and emptied my thrash, so that is not it.

---

### Post by MrWES on 2009-06-16
> **jlbr21 said:**
> Hi, I have been trying to install some stuff, like python scripts for Gimp, and I kept getting the message that there was no space left, then I checked and it seems like my root partition is full!

I have 9.4 gb as root partition, and I cant seem to find the file(s) that are clogging up my root partition.

Please help.

BTW, I have apt-get clean'ed and emptied my thrash, so that is not it.

Try running the disk usage analyzer found in Applications | Accessories.

Also did you run a 
```
sudo apt-get autoremove
```?

Bill

---

### Post by abhiroopb on 2009-06-16
could be a number of things...

1. /tmp (temporary folder) is full...but this is unlikely

2. you copied something to external media, while there was nothing plugged in...so instead of copying to the external media, it copied into your root folder.

List the contents of /tmp and list the contents of /mnt and /media

---

### Post by swisstone198 on 2009-06-16
As root user from / run

# du -sm *

This will tell you the size off all directories then go down from there.

Or run 

# find / -size +1000000c -ls

(change the number of zero's till you get a reasonable number of files.)


EDIT

add -mount to stay on the root filesystem

eg

# find / -mount -size +1000000c -ls

---

### Post by lamego on 2009-06-16
On the terminal type:
```
sudo du -sh /*
```

---

### Post by jlbr21 on 2009-06-16
OK, here it goes:
> juanluis@juanluis-laptop ~ $ cd /media
juanluis@juanluis-laptop /media $ ls
cdrom  cdrom0  cdrom1  disk
juanluis@juanluis-laptop /media $ 
> 
juanluis@juanluis-laptop /media $ cd /mnt
juanluis@juanluis-laptop /mnt $ ls
ipod
juanluis@juanluis-laptop /mnt $ cd ipod
juanluis@juanluis-laptop /mnt/ipod $ ls
juanluis@juanluis-laptop /mnt/ipod $ 

> juanluis@juanluis-laptop /tmp $ ls
keyring-gzHBvC  orbit-juanluis  seahorse-mANJOB        virtual-juanluis.kvGa57
mplayWGodow     pulse-juanluis  Tracker-juanluis.6372


Now, the ipod folder is empty, the disk in the media refers to a usb memory stick.

Ok, now I will do what swisstone198 says. just a minute.

---

### Post by jlbr21 on 2009-06-16
> juanluis@juanluis-laptop ~ $ sudo du -sh /*
7.3M	/bin
14M	/boot
0	/cdrom
3.4M	/dev
13M	/etc
du: cannot access `/home/juanluis/.gvfs': Permission denied
40G	/home
0	/initrd.img
145M	/lib
4.4M	/lib32
0	/lib64
16K	/lost+found
6.4G	/media
8.0K	/mnt
9.1M	/opt
du: cannot access `/proc/6810/task/6810/fd/4': No such file or directory
du: cannot access `/proc/6810/task/6810/fdinfo/4': No such file or directory
du: cannot access `/proc/6810/fd/4': No such file or directory
du: cannot access `/proc/6810/fdinfo/4': No such file or directory
0	/proc
332K	/root
11M	/sbin
4.0K	/srv
0	/sys
36K	/tmp
2.2G	/usr
6.5G	/var
0	/vmlinuz

OK, what should I do now?

---

### Post by halitech on 2009-06-16
/var seems to be where you have most of your space being used. whats the output of
```
sudo du -h /var/log
```

---

### Post by jlbr21 on 2009-06-16
> juanluis@juanluis-laptop ~ $ sudo du -h /var/log
4.0K	/var/log/news
28K	/var/log/gdm
144K	/var/log/cups
148K	/var/log/ConsoleKit
4.0K	/var/log/unattended-upgrades
375M	/var/log/installer
4.0K	/var/log/samba/cores/smbd
4.0K	/var/log/samba/cores/nmbd
12K	/var/log/samba/cores
52K	/var/log/samba
156K	/var/log/apt
12K	/var/log/fsck
6.2G	/var/log

/var/log/ is strangely big, right? can I wipe out the content? what is var anyway?

---

### Post by drs305 on 2009-06-16
If you cannot find the problem please refer to this wiki. It covers the common reasons for lost disk space, how to find out what is causing it and how to recover it.

Your /var/log files appear to be very large. See what's in there. 

The link to the wiki is in my signature line or here:
[https://help.ubuntu.com/community/RecoverLostDiskSpace]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

---

### Post by halitech on 2009-06-16
/var/log is extremely large, mine is 9.3meg. 

I wouldn't just randomly delete files in there but post the output of
```
ls /var/log -l
``` and we'll see what you can delete

---

### Post by jlbr21 on 2009-06-16
> juanluis@juanluis-laptop /var/log $ ls
apt                 dpkg.log              samba
aptitude            dpkg.log.1            syslog
aptitude.1.gz       faillog               syslog.0
auth.log            fontconfig.log        syslog.1.gz
auth.log.0          fsck                  syslog.2.gz
auth.log.1.gz       gdm                   syslog.3.gz
auth.log.2.gz       installer             syslog.4.gz
boot                kern.log              syslog.5.gz
bootstrap.log       kern.log.0            syslog.6.gz
btmp                kern.log.1.gz         udev
btmp.1              kern.log.2.gz         unattended-upgrades
ConsoleKit          kern.log.3.gz         user.log
cups                kern.log.4.gz         user.log.0
daemon.log          lastlog               user.log.1.gz
daemon.log.0        lpr.log               user.log.2.gz
daemon.log.1.gz     mail.err              vbox-install.log
daemon.log.2.gz     mail.info             wpa_supplicant.log
debug               mail.log              wpa_supplicant.log.1.gz
debug.0             mail.warn             wpa_supplicant.log.2.gz
debug.1.gz          messages              wpa_supplicant.log.3.gz
debug.2.gz          messages.0            wpa_supplicant.log.4.gz
dkms_autoinstaller  messages.1.gz         wpa_supplicant.log.5.gz
dmesg               messages.2.gz         wtmp
dmesg.0             messages.3.gz         wtmp.1
dmesg.1.gz          mintUpdate.history    wvdialconf.log
dmesg.2.gz          news                  Xorg.0.log
dmesg.3.gz          nvidia-installer.log  Xorg.0.log.old
dmesg.4.gz          pycentral.log         Xorg.failsafe.log


OK, Im taking a look at the Wiki now, these are the contents of var/log, I have no idea if or what are these files really.
Thanks for the help.

---

### Post by jlbr21 on 2009-06-16
juanluis@juanluis-laptop /var $ ls /var/log -l
total 6050968
drwxr-xr-x 2 root   root       4096 2009-06-01 15:26 apt
-rw-r--r-- 1 root   root       1866 2009-06-11 08:05 aptitude
-rw-r--r-- 1 root   root       1993 2009-02-02 14:43 aptitude.1.gz
-rw-r----- 1 syslog adm       24576 2009-06-16 20:04 auth.log
-rw-r----- 1 syslog adm       59592 2009-06-13 10:04 auth.log.0
-rw-r----- 1 syslog adm        5435 2009-06-06 09:50 auth.log.1.gz
-rw-r----- 1 syslog adm         734 2009-05-30 08:30 auth.log.2.gz
-rw-r----- 1 root   adm          31 2008-10-29 15:05 boot
-rw-r--r-- 1 root   root      36637 2008-10-29 15:06 bootstrap.log
-rw-rw-r-- 1 root   utmp        768 2009-06-15 16:45 btmp
-rw-rw-r-- 1 root   utmp        384 2009-05-30 09:00 btmp.1
drwxr-xr-x 2 root   root       4096 2009-05-30 08:29 ConsoleKit
drwxr-xr-x 2 root   root       4096 2009-06-15 17:06 cups
-rw-r----- 1 syslog adm      311296 2009-06-16 20:03 daemon.log
-rw-r----- 1 syslog adm      594649 2009-06-13 10:00 daemon.log.0
-rw-r----- 1 syslog adm       57775 2009-06-06 09:50 daemon.log.1.gz
-rw-r----- 1 syslog adm        2954 2009-05-30 08:30 daemon.log.2.gz
-rw-r----- 1 syslog adm      880640 2009-06-16 19:43 debug
-rw-r----- 1 syslog adm      443650 2009-06-13 09:57 debug.0
-rw-r----- 1 syslog adm       49532 2009-06-06 09:47 debug.1.gz
-rw-r----- 1 syslog adm        2823 2009-05-30 08:30 debug.2.gz
-rw-r--r-- 1 root   root       8586 2009-06-16 19:42 dkms_autoinstaller
-rw-r----- 1 root   adm       50240 2009-06-16 19:42 dmesg
-rw-r----- 1 root   adm       50152 2009-06-16 16:29 dmesg.0
-rw-r----- 1 root   adm       12300 2009-06-16 15:40 dmesg.1.gz
-rw-r----- 1 root   adm       12368 2009-06-15 21:19 dmesg.2.gz
-rw-r----- 1 root   adm       12383 2009-06-15 16:39 dmesg.3.gz
-rw-r----- 1 root   adm       12401 2009-06-15 16:33 dmesg.4.gz
-rw-r----- 1 root   adm      128219 2009-06-16 16:11 dpkg.log
-rw-r----- 1 root   adm     1342211 2009-05-31 21:19 dpkg.log.1
-rw-r--r-- 1 root   root      32032 2009-05-30 08:21 faillog
-rw-r--r-- 1 root   root       2587 2008-12-28 17:11 fontconfig.log
drwxr-xr-x 2 root   root       4096 2008-10-29 15:05 fsck
drwxr-xr-x 2 root   root       4096 2009-06-16 19:42 gdm
drwxr-xr-x 2 root   root       4096 2009-05-30 08:26 installer
-rw-r----- 1 syslog adm  2120589312 2009-06-16 20:03 kern.log
-rw-r----- 1 syslog adm      572045 2009-06-13 10:03 kern.log.0
-rw-r----- 1 syslog adm      176009 2009-06-10 18:17 kern.log.1.gz
-rw-r----- 1 syslog adm       85947 2009-06-06 09:52 kern.log.2.gz
-rw-r----- 1 syslog adm      168102 2009-06-04 08:03 kern.log.3.gz
-rw-r----- 1 syslog adm       13711 2009-05-30 08:30 kern.log.4.gz
-rw-rw-r-- 1 root   utmp     292292 2009-05-30 08:21 lastlog
-rw-r----- 1 syslog adm           0 2008-10-29 15:05 lpr.log
-rw-r----- 1 syslog adm           0 2008-10-29 15:05 mail.err
-rw-r----- 1 syslog adm           0 2008-10-29 15:05 mail.info
-rw-r----- 1 syslog adm           0 2008-10-29 15:05 mail.log
-rw-r----- 1 syslog adm           0 2008-10-29 15:05 mail.warn
-rw-r----- 1 syslog adm  1941778432 2009-06-16 20:03 messages
-rw-r----- 1 syslog adm       65824 2009-06-13 10:08 messages.0
-rw-r----- 1 syslog adm      204751 2009-06-12 17:01 messages.1.gz
-rw-r----- 1 syslog adm      176148 2009-06-06 09:52 messages.2.gz
-rw-r----- 1 syslog adm      183595 2009-06-01 15:26 messages.3.gz
-rw-r--r-- 1 root   root      21366 2009-06-09 17:47 mintUpdate.history
drwxr-sr-x 2 news   news       4096 2009-05-30 08:29 news
-rw-r--r-- 1 root   root       2145 2009-05-31 09:52 nvidia-installer.log
-rw-r--r-- 1 root   root          0 2008-10-29 15:10 pycentral.log
drwxr-x--- 3 root   adm        4096 2009-06-15 18:13 samba
-rw-r----- 1 syslog adm  2120220672 2009-06-16 20:03 syslog
-rw-r----- 1 syslog adm      289176 2009-06-15 17:03 syslog.0
-rw-r----- 1 syslog adm       60518 2009-06-14 10:03 syslog.1.gz
-rw-r----- 1 syslog adm       20308 2009-06-13 10:03 syslog.2.gz
-rw-r----- 1 syslog adm       63345 2009-06-12 17:06 syslog.3.gz
-rw-r----- 1 syslog adm       37949 2009-06-11 08:07 syslog.4.gz
-rw-r----- 1 syslog adm       77868 2009-06-10 18:37 syslog.5.gz
-rw-r----- 1 syslog adm       38991 2009-06-09 17:24 syslog.6.gz
-rw-r--r-- 1 root   root     448409 2009-06-16 19:42 udev
drwxr-xr-x 2 root   root       4096 2008-10-13 06:52 unattended-upgrades
-rw-r----- 1 syslog adm        8172 2009-06-16 19:43 user.log
-rw-r----- 1 syslog adm       40237 2009-06-13 09:57 user.log.0
-rw-r----- 1 syslog adm        2687 2009-06-06 09:47 user.log.1.gz
-rw-r----- 1 syslog adm         286 2009-05-30 08:29 user.log.2.gz
-rw-r--r-- 1 root   root       1433 2009-05-30 09:16 vbox-install.log
-rw-r--r-- 1 root   root      10263 2009-06-16 20:14 wpa_supplicant.log
-rw-r--r-- 1 root   root        418 2009-06-15 17:05 wpa_supplicant.log.1.gz
-rw-r--r-- 1 root   root        469 2009-06-14 10:05 wpa_supplicant.log.2.gz
-rw-r--r-- 1 root   root        277 2009-06-13 10:07 wpa_supplicant.log.3.gz
-rw-r--r-- 1 root   root        455 2009-06-12 17:14 wpa_supplicant.log.4.gz
-rw-r--r-- 1 root   root        306 2009-06-11 08:07 wpa_supplicant.log.5.gz
-rw-rw-r-- 1 root   utmp     184320 2009-06-16 20:09 wtmp
-rw-rw-r-- 1 root   utmp      75264 2009-06-01 15:25 wtmp.1
-rw-r--r-- 1 root   root        308 2008-10-29 15:25 wvdialconf.log
-rw-r--r-- 1 root   root      15465 2009-06-16 19:43 Xorg.0.log
-rw-r--r-- 1 root   root      15794 2009-06-16 16:59 Xorg.0.log.old
-rw-r--r-- 1 root   root      38899 2009-05-30 10:06 Xorg.failsafe.log

---

### Post by drs305 on 2009-06-16
This would give you a bit easier depiction:
```

du -h  --max-depth=2 /var/log | sort

```
Added: you can start the command with "sudo" to prevent some "permission denied" messages.

The wiki would eventually take you to the /var/ folder, since it contains 6GB of a 9GB install, which is very abnormal. Now you just have to find out which logs are taking up the most space.

For any of the logs, if there are multiples you can safely delete them, especially the older .gz ones. 

Note on deleting these folders. Use "gksudo nautilus /var/log" and use SHIFT-DEL to delete what you decide to get rid of. If you just hit DEL, it will place the contents in root's trash bin but it will reside there and take up space until the Trash is emptied.  Use caution, however, as SHIFT-DEL cannot be easily reversed.

---

### Post by halitech on 2009-06-16
here's some info on /var/log

[http://ubuntuforums.org/showthread.php?t=232551](http://ubuntuforums.org/showthread.php?t=232551)

seems any .gz files can be safely deleted at least. I'm curious about these ones though

-rw-r----- 1 syslog adm 2120589312 2009-06-16 20:03 kern.log
-rw-r----- 1 syslog adm 1941778432 2009-06-16 20:03 messages
-rw-r----- 1 syslog adm 2120220672 2009-06-16 20:03 syslog

and why they are so large

---

### Post by lloyd_b on 2009-06-16
> **jlbr21 said:**
> juanluis@juanluis-laptop /var $ ls /var/log -l
total 6050968

-rw-r----- 1 syslog adm  2120589312 2009-06-16 20:03 kern.log
-rw-r----- 1 syslog adm  1941778432 2009-06-16 20:03 messages
-rw-r----- 1 syslog adm  2120220672 2009-06-16 20:03 syslog


Those three are the problem - Between them they're accounting for over 6GB of disk space.

You need to look at those files, and see what's going on.  It sounds like some event is happening over and over at a very rapid pace, and the logs are recording very large numbers of these events.  So the out-of-diskspace condition isn't the root problem - it's just a symptom of something else.

Try "tail -n 25 <file>", substituting the correct file name, and see what it tells you.

Note that if you boot the machine in recovery mode, you can safely delete those files.  But you need to sort out *why* they're growing so big first, otherwise it'll just happen again.

Lloyd B.

---

### Post by Rubicon_82 on 2009-06-16
> 
-rw-r----- 1 syslog adm  2120220672 2009-06-16 20:03 syslog
-rw-r----- 1 syslog adm      289176 2009-06-15 17:03 syslog.0
-rw-r----- 1 syslog adm       60518 2009-06-14 10:03 syslog.1.gz
-rw-r----- 1 syslog adm       20308 2009-06-13 10:03 syslog.2.gz
Judging by the size of the previous syslogs, this is something that has started happening in the last day or so.

Did you install any new packages, or modify the configuration of any existing packages in the last two days?

---

### Post by jlbr21 on 2009-06-16
Yeah, well, I wouldn't be the guy to ask why they are, were so large, I just wiped them out out of desperation, I had not seen those last two posts.

Sure enough, the root partition is now down to 35% full.

Hope I did not make a mistake in erasing them...

The only clue I have as to why they grow is my nvidia configuration, I have had many issues with the config. of the card, and the dual monitor I have now. Maybe everytime I log in the xorg file and other stuff creates logs??

No clue.

---

### Post by lloyd_b on 2009-06-16
> **jlbr21 said:**
> Yeah, well, I wouldn't be the guy to ask why they are, were so large, I just wiped them out out of desperation, I had not seen those last two posts.

Sure enough, the root partition is now down to 35% full.

Hope I did not make a mistake in erasing them...

The only clue I have as to why they grow is my nvidia configuration, I have had many issues with the config. of the card, and the dual monitor I have now. Maybe everytime I log in the xorg file and other stuff creates logs??

No clue.

Those log files are recreated by the system on every boot, if they don't already exist.  That's perfectly normal.  What's not normal is the size of them...

Keep an eye on those files.  If they start growing again (which is quite possible, since we haven't resolved the root problem), then look in them for one or a few messages that seem to be repeated over and over.  Post those messages, and we may be able to help sort the problem out (though once you've identified the problem message(s), you'll probably get better results if you open up a new thread with a title appropriate to the message).

Lloyd B.

---

### Post by Celauran on 2009-06-16
In fact, I'd look at them ASAP before they become obscenely large.

---

### Post by ericab on 2009-06-16
im really curious to see the contents of the logs myself.
do tell!

---

### Post by jlbr21 on 2009-06-16
yep, the kern.log.0 is already growing, here is the content of it, sorry for the lenght of it:

[QUOTE]Jun 10 19:32:59 juanluis-laptop kernel: Inspecting /boot/System.map-2.6.27-7-generic
Jun 10 19:32:59 juanluis-laptop kernel: Cannot find map file.
Jun 10 19:32:59 juanluis-laptop kernel: Loaded 75851 symbols from 101 modules.
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Command line: root=/dev/sda5 ro quiet splash
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] KERNEL supported cpus:
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   Intel GenuineIntel
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   AMD AuthenticAMD
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   Centaur CentaurHauls
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 000000000009e000 - 00000000000a0000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000be624000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000be624000 - 00000000be627000 (ACPI NVS)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000be627000 - 00000000bfca8000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfca8000 - 00000000bfcbf000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfcbf000 - 00000000bfd86000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfd86000 - 00000000bfdbf000 (ACPI NVS)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfdbf000 - 00000000bfdea000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfdea000 - 00000000bfdff000 (ACPI data)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfdff000 - 00000000bfe00000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000bfe00000 - 00000000c0000000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x3ffffffff
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] last_pfn = 0xbfe00 max_arch_pfn = 0x3ffffffff
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] init_memory_mapping
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] kernel direct mapping tables up to bfe00000 @ 8000-c000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] last_map_addr: bfe00000 end: bfe00000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] init_memory_mapping
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  0100000000 - 0140000000 page 2M
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] last_map_addr: 140000000 end: 140000000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] RAMDISK: 376fb000 - 37feff74
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] DMI 2.4 present.
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: RSDP 000FE020, 0024 (r2 HPQOEM)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: XSDT BFDFE120, 0064 (r1 HPQOEM SLIC-MPC        1       1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: FACP BFDFD000, 00F4 (r4 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: DSDT BFDED000, B31E (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: FACS BFD92000, 0040
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: HPET BFDFC000, 0038 (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: APIC BFDFB000, 006C (r2 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: MCFG BFDFA000, 003C (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: ASF! BFDF9000, 00A5 (r32 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: SLIC BFDEC000, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: BOOT BFDEB000, 0028 (r1 HPQOEM SLIC-MPC        1 MSFT  1000013)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: SSDT BFDEA000, 0655 (r1  PmRef    CpuPm     3000 INTL 20051117)
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] No NUMA configuration found
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Faking a node at 0000000000000000-0000000140000000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   bootmap [000000000000b000 -  0000000000032fff] pages 28
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0140000000]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #2 [0000200000 - 00008b8f9c]    TEXT DATA BSS ==> [0000200000 - 00008b8f9c]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #3 [00376fb000 - 0037feff74]          RAMDISK ==> [00376fb000 - 0037feff74]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #4 [000009e000 - 0000100000]    BIOS reserved ==> [000009e000 - 0000100000]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #5 [0000008000 - 000000a000]          PGTABLE ==> [0000008000 - 000000a000]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   #6 [000000a000 - 000000b000]          PGTABLE ==> [000000a000 - 000000b000]
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Zone PFN ranges:
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]   Normal   0x00100000 -> 0x00140000
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000] early_node_map[7] active PFN ranges
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009e
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x000be624
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]     0: 0x000be627 -> 0x000bfca8
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]     0: 0x000bfcbf -> 0x000bfd86
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]     0: 0x000bfdbf -> 0x000bfdea
Jun 10 19:32:59 juanluis-laptop kernel: [    0.000000]     0: 0x000bfdff -> 0x000bfe00


This is just a small (very small) fragment. I cannot post all of the text, it's so large the forum won't allow me. It seems many combos of characters get interpreted as smileys and the system wont let me post more than 8 (?)
I can post more of the content, but there's definitely something wrong here...Im worried now

---

### Post by lloyd_b on 2009-06-16
> **ericab said:**
> im really curious to see the contents of the logs myself.
do tell!

To tell the truth, so am I.  The only time I've seen log files grow like that was a case where a terminal server was flaky, and it was connecting and disconnecting at a rate of several times per second.  The kernel basically spammed the log files with all of those connect/disconnect messages.

Lloyd B.

---

### Post by Celauran on 2009-06-16
> **jlbr21 said:**
> 
I can post more of the content, but there's definitely something wrong here...Im worried now

The machine is still working, you're still able to log in. That's already a good thing. Maybe attach/upload the files so we can take a peek?

---

### Post by jlbr21 on 2009-06-16
This is a fragment of the debug.log file. It is also strangely large, almost a MB

> Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000]  0000000000 - 00bfe00000 page 2M
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] kernel direct mapping tables up to bfe00000 @ 8000-c000
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000]  0100000000 - 0140000000 page 2M
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] kernel direct mapping tables up to 140000000 @ a000-10000
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000]  [ffffe20000000000-ffffe20004ffffff] PMD -> [ffff880028200000-ffff88002c1fffff] on node 0
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] On node 0 totalpages: 1047862
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000]   DMA zone: 2110 pages, LIFO batch:0
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000]   DMA32 zone: 765400 pages, LIFO batch:31
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000]   Normal zone: 258048 pages, LIFO batch:31
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] ACPI: IRQ0 used by override.
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] ACPI: IRQ2 used by override.
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] ACPI: IRQ9 used by override.
Jun 13 12:18:51 juanluis-laptop kernel: [    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
Jun 13 12:18:51 juanluis-laptop kernel: [    0.004000] Calgary: detecting Calgary via BIOS EBDA area
Jun 13 12:18:51 juanluis-laptop kernel: [    0.004000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jun 13 12:18:51 juanluis-laptop kernel: [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
Jun 13 12:18:51 juanluis-laptop kernel: [    0.004000] hpet clockevent registered
Jun 13 12:18:51 juanluis-laptop kernel: [    0.416027] APIC timer calibration result 16626852
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508106] CPU0 attaching sched-domain:
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508108]  domain 0: span 0-1 level MC
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508111]   groups: 0 1
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508114]   domain 1: span 0-1 level NODE
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508115]    groups: 0-1
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508119] CPU1 attaching sched-domain:
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508120]  domain 0: span 0-1 level MC
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508122]   groups: 1 0
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508124]   domain 1: span 0-1 level NODE
Jun 13 12:18:51 juanluis-laptop kernel: [    0.508126]    groups: 0-1
Jun 13 12:18:51 juanluis-laptop kernel: [    0.513212] ACPI: EC: Look up EC in DSDT
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676304] PCI: 0000:00:1a.0 reg 20 io port: [a0e0, a0ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676304] PCI: 0000:00:1a.1 reg 20 io port: [a0c0, a0df]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676304] PCI: 0000:00:1a.7 reg 10 32bit mmio: [df305c00, df305fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676352] PCI: 0000:00:1b.0 reg 10 64bit mmio: [df300000, df303fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676698] PCI: 0000:00:1d.0 reg 20 io port: [a0a0, a0bf]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676754] PCI: 0000:00:1d.1 reg 20 io port: [a080, a09f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676810] PCI: 0000:00:1d.2 reg 20 io port: [a060, a07f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676867] PCI: 0000:00:1d.3 reg 20 io port: [a040, a05f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.676926] PCI: 0000:00:1d.7 reg 10 32bit mmio: [df305800, df305bff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677111] PCI: 0000:00:1f.2 reg 10 io port: [a108, a10f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677116] PCI: 0000:00:1f.2 reg 14 io port: [a114, a117]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677121] PCI: 0000:00:1f.2 reg 18 io port: [a100, a107]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677125] PCI: 0000:00:1f.2 reg 1c io port: [a110, a113]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677130] PCI: 0000:00:1f.2 reg 20 io port: [a020, a03f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677135] PCI: 0000:00:1f.2 reg 24 32bit mmio: [df305000, df3057ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677176] PCI: 0000:00:1f.3 reg 10 64bit mmio: [df306000, df3060ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677188] PCI: 0000:00:1f.3 reg 20 io port: [a000, a01f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677235] PCI: 0000:00:1f.6 reg 10 64bit mmio: [df304000, df304fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677343] PCI: 0000:01:00.0 reg 10 32bit mmio: [d2000000, d2ffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677357] PCI: 0000:01:00.0 reg 14 32bit mmio: [c0000000, cfffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677383] PCI: 0000:01:00.0 reg 1c 64bit mmio: [d0000000, d1ffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677396] PCI: 0000:01:00.0 reg 24 io port: [9000, 907f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677410] PCI: 0000:01:00.0 reg 30 32bit mmio: [fff80000, ffffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677479] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677481] PCI: bridge 0000:00:01.0 32bit mmio: [d0000000, d2ffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677485] PCI: bridge 0000:00:01.0 64bit mmio pref: [c0000000, cfffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677554] PCI: 0000:02:00.0 reg 10 64bit mmio: [de200000, de201fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677666] PCI: bridge 0000:00:1c.0 io port: [8000, 8fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677669] PCI: bridge 0000:00:1c.0 32bit mmio: [de200000, df2fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677674] PCI: bridge 0000:00:1c.0 64bit mmio pref: [d3000000, d3ffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677716] PCI: 0000:03:00.0 reg 10 io port: [6000, 60ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677729] PCI: 0000:03:00.0 reg 18 32bit mmio: [d4010000, d4010fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677743] PCI: 0000:03:00.0 reg 20 32bit mmio: [d4000000, d400ffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677756] PCI: 0000:03:00.0 reg 30 32bit mmio: [ffff0000, ffffffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677782] pci 0000:03:00.0: supports D1
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677783] pci 0000:03:00.0: supports D2
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677819] PCI: bridge 0000:00:1c.1 io port: [6000, 7fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677822] PCI: bridge 0000:00:1c.1 32bit mmio: [dd200000, de1fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677827] PCI: bridge 0000:00:1c.1 64bit mmio pref: [d4000000, d50fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677863] PCI: bridge 0000:00:1c.2 io port: [5000, 5fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677866] PCI: bridge 0000:00:1c.2 32bit mmio: [dc200000, dd1fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677871] PCI: bridge 0000:00:1c.2 64bit mmio pref: [d5100000, d60fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677906] PCI: bridge 0000:00:1c.3 io port: [4000, 4fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677909] PCI: bridge 0000:00:1c.3 32bit mmio: [db200000, dc1fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677915] PCI: bridge 0000:00:1c.3 64bit mmio pref: [d6100000, d70fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677963] PCI: 0000:06:00.0 reg 10 32bit mmio: [da100000, da1007ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677972] PCI: 0000:06:00.0 reg 14 32bit mmio: [da100d00, da100d7f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.677999] PCI: 0000:06:00.0 reg 20 32bit mmio: [da100c80, da100cff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678008] PCI: 0000:06:00.0 reg 24 32bit mmio: [da100c00, da100c7f]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678081] PCI: 0000:06:00.1 reg 10 32bit mmio: [da100b00, da100bff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678183] PCI: 0000:06:00.2 reg 10 32bit mmio: [da100a00, da100aff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678285] PCI: 0000:06:00.3 reg 10 32bit mmio: [da100900, da1009ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678386] PCI: 0000:06:00.4 reg 10 32bit mmio: [da100800, da1008ff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678486] PCI: bridge 0000:00:1c.4 io port: [3000, 3fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678489] PCI: bridge 0000:00:1c.4 32bit mmio: [da100000, db1fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678494] PCI: bridge 0000:00:1c.4 64bit mmio pref: [d7100000, d80fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678530] PCI: bridge 0000:00:1c.5 io port: [2000, 2fff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678533] PCI: bridge 0000:00:1c.5 32bit mmio: [d9100000, da0fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678538] PCI: bridge 0000:00:1c.5 64bit mmio pref: [d8100000, d90fffff]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.678628] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.679129] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.679299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.679539] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.680227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.680429] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.680627] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.680824] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP5._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.681047] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
Jun 13 12:18:51 juanluis-laptop kernel: [    0.708039] Switched to high resolution mode on CPU 0
Jun 13 12:18:51 juanluis-laptop kernel: [    0.708672] Switched to high resolution mode on CPU 1
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725186] pci 0000:00:01.0: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725196] pci 0000:00:1c.0: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725205] pci 0000:00:1c.1: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725218] pci 0000:00:1c.2: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725231] pci 0000:00:1c.3: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725240] pci 0000:00:1c.4: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725250] pci 0000:00:1c.5: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    0.725255] pci 0000:00:1e.0: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511440] pci 0000:01:00.0: Boot video device
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511552] pcieport-driver 0000:00:01.0: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511605] pci_express 0000:00:01.0:pcie00: allocate port service
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511640] pci_express 0000:00:01.0:pcie02: allocate port service
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511674] pci_express 0000:00:01.0:pcie03: allocate port service
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511743] pcieport-driver 0000:00:1c.0: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511801] pci_express 0000:00:1c.0:pcie00: allocate port service
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511835] pci_express 0000:00:1c.0:pcie02: allocate port service
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511867] pci_express 0000:00:1c.0:pcie03: allocate port service
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511941] pcieport-driver 0000:00:1c.1: setting latency timer to 64
Jun 13 12:18:51 juanluis-laptop kernel: [    1.511999] pci_express 

---

### Post by lloyd_b on 2009-06-16
> **jlbr21 said:**
> yep, the kern.log.0 is already growing, here is the content of it, sorry for the lenght of it:

This is just a small (very small) fragment. I cannot post all of the text, it's so large the forum won't allow me. It seems many combos of characters get interpreted as smileys and the system wont let me post more than 8 (?)
I can post more of the content, but there's definitely something wrong here...Im worried now

What will be most interesting will be towards the end of the log file, not the beginning.  The thing to look for are repeating entries.

The "tail" command allows you to grab the last n lines of a file.  So "tail -n 25 <file>" will display the last 25 lines of the file to the terminal.  

Note that just because the files are growing isn't cause for alarm - those log files *always* grow continuously.  It's the rate at which they grow that should be of concern.  For example, how large are those 3 files now?

Lloyd B.

---

### Post by ericab on 2009-06-16
if ti was me; by this point i would have:

1)
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

2)
reinstalled.

listen to lloyd_b though, as i have no clue as to the cause.

---

### Post by jlbr21 on 2009-06-16
it seems these attached files and others (like messages.log) are constantly growing, they are already about 1 MB each. I had to turn them into zip files cause they are too large to be uploaded as txt files.

what is going on?

Yes, the computer acts as if nothing was happening, and i have not done anything or installed anything relevant that I can remember.

---

### Post by Celauran on 2009-06-16
kern.log stops at June 13.

In debug.log, I'm seeing lots of:

```
Jun 16 20:44:52 juanluis-laptop kernel: [    1.524796] pcieport-driver 0000:00:1c.5: setting latency timer to 64
Jun 16 20:44:52 juanluis-laptop kernel: [    1.524854] pci_express 0000:00:1c.5:pcie00: allocate port service
Jun 16 20:44:52 juanluis-laptop kernel: [    1.524891] pci_express 0000:00:1c.5:pcie02: allocate port service
Jun 16 20:44:52 juanluis-laptop kernel: [    1.524923] pci_express 0000:00:1c.5:pcie03: allocate port service
```

and lots of:

```
Jun 16 20:44:52 juanluis-laptop kernel: [    0.677965] PCI: 0000:06:00.0 reg 10 32bit mmio: [da100000, da1007ff]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.677975] PCI: 0000:06:00.0 reg 14 32bit mmio: [da100d00, da100d7f]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.678001] PCI: 0000:06:00.0 reg 20 32bit mmio: [da100c80, da100cff]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.678011] PCI: 0000:06:00.0 reg 24 32bit mmio: [da100c00, da100c7f]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.678084] PCI: 0000:06:00.1 reg 10 32bit mmio: [da100b00, da100bff]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.678186] PCI: 0000:06:00.2 reg 10 32bit mmio: [da100a00, da100aff]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.678289] PCI: 0000:06:00.3 reg 10 32bit mmio: [da100900, da1009ff]
Jun 16 20:44:52 juanluis-laptop kernel: [    0.678391] PCI: 0000:06:00.4 reg 10 32bit mmio: [da100800, da1008ff]

```

Sadly, neither means anything to me and Google hasn't turned up anything yet. Maybe it looks familiar to someone else, though.

EDIT: Actually, you mentioned something about trouble with your video card. Anything unusual in lspci?

---

### Post by jlbr21 on 2009-06-16
Gosh, i hhave no clue as to what the problem could be...

It's late already, have to go and get some sleep.

Thanks for your help.

---

### Post by lloyd_b on 2009-06-17
looking at debug.txt, the following caught my eye:```
Jun 15 19:27:21 juanluis-laptop kernel: >>[10071.431441] bad: scheduling from the idle thread!
Jun 15 19:27:21 juanluis-laptop kernel: >>[10071.431713] bad: scheduling from the idle thread!
Jun 15 19:27:21 juanluis-laptop kernel: >>[10071.431985] bad: scheduling from the idle thread!
Jun 15 19:27:21 juanluis-laptop kernel: >>[10071.432259] bad: scheduling from the idle thread!
```

Did a Google search on it, and turned up [this link]("https://bugs.launchpad.net/ubuntu/+bug/289581") on Launchpad.  Apparently, this is a known kernel bug, that produces exactly the symptoms you've reported.  All of the bug reports appear to be for Intrepid, though.  What *buntu version are you running?

I'm afraid I'm not going to be any further help - this appears to be an issue somewhere in the kernel, which is WAY beyond my skill range.  

I *would* recommend following ericab's suggestion, and have a good backup on that machine (at least of any critical data), just in case.

Lloyd B.

---

### Post by drs305 on 2009-06-17
In view of the past several posts, I would recommend either updating to a newer kernel (if available) or reverting to an older kernel if one is still listed in your grub menu.lst  

Delete the log files if you can change kernels and see if they continue to grow with a different kernel.

Oh, and for the forums, if you want to post some content but get "smileys" you can put the offending text within the following. I can't exactly duplicate it so you would have to remove the space after the right **[COLOR="DarkRed"][[/COLOR]** 's:

**[COLOR="DarkRed"][[/COLOR]** noparse]text here **[COLOR="DarkRed"][[/COLOR]** /noparse]

---

### Post by H2SO_four on 2009-06-17
> **drs305 said:**
> in view of the past several posts, i would recommend either updating to a newer kernel (if available) or reverting to an older kernel if one is still listed in your grub menu.lst  

delete the log files if you can change kernels and see if they continue to grow with a different kernel.

Oh, and for the forums, if you want to post some content but get "smileys" you can put the offending text within the following. I can't exactly duplicate it so you would have to remove the space after the right **[color="darkred"][[/color]** 's:

**[color="darkred"][[/color]** noparse]text here **[color="darkred"][[/color]** /noparse]

+1

---

### Post by halitech on 2009-06-17
> **drs305 said:**
> In view of the past several posts, I would recommend either updating to a newer kernel (if available) or reverting to an older kernel if one is still listed in your grub menu.lst  

Delete the log files if you can change kernels and see if they continue to grow with a different kernel.

Oh, and for the forums, if you want to post some content but get "smileys" you can put the offending text within the following. I can't exactly duplicate it so you would have to remove the space after the right **[COLOR="DarkRed"][[/COLOR]** 's:

**[COLOR="DarkRed"][[/COLOR]** noparse]text here **[COLOR="DarkRed"][[/COLOR]** /noparse]

there is also an option in the quote reply to disable smilies under additional options. I would guess its there on new posts as well but not on quick reply options.

---

