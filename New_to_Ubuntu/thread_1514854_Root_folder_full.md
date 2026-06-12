---
title: "Root folder full?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by archkidd on 2010-06-21
Update Manager just finished and I received a message that my root folder has only 800MB space left.  The disk usage analyser shows that I have a 9.4GB root folder.  My hard drive is 53GB with 30GB free space.  I only have Ubuntu 10.4 loaded with very few additional programs.  File Browser won't let me look in the root folder so I don't know what is in there.  What do I do?  What capacity should I make the root folder and how.  I have gparted if that is what I need to change my partitions?
Thanks

---

### Post by sanderj on 2010-06-21
Start "Disk Usage Analyzer" (Applications -> Accessories -> Disk Usage Analyzer) to see what is using your disk space.

---

### Post by archkidd on 2010-06-21
I did that.  It shows the / folder as 100% with 9.4GB and 20 items, the 'Home' folder as 67%, 2 items and 6.4GB, and 'usr' as 25.7%, 2.4GB and 8 items.

---

### Post by philinux on 2010-06-21
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by archkidd on 2010-06-21
By using System Monitor I now understand that all my files are in my /dev/sda1 partition which is now full while my /dev/sda5 partition has 30GB of free space.  I thought that all my files were in that partition but obviously not.  It does not even show in my browser.  How do I move my file folders over to this sda5 partition?

---

### Post by sanderj on 2010-06-21
> **archkidd said:**
> I did that.  It shows the / folder as 100% with 9.4GB and 20 items, the 'Home' folder as 67%, 2 items and 6.4GB, and 'usr' as 25.7%, 2.4GB and 8 items.

Press "CTRL F" to scan the whole file system and see the details.

---

### Post by sanderj on 2010-06-21
Or, if you prefer one-liners:

```

sudo du -BM /  | egrep -vi -e "^[0-9]M" -e "^[0-9][0-9]M" -e home -e proc -e media


```

which on my computer leads to this (hopefully useful) output:

```

sander@athlon64:~$ sudo du -BM /  | egrep -vi -e "^[0-9]M" -e "^[0-9][0-9]M" -e home -e proc -e media
323M	/var/cache/apt/archives
369M	/var/cache/apt
393M	/var/cache
223M	/var/lib
652M	/var
du: cannot access `/home/sander/.gvfs': Permission denied
103M	/opt/google/picasa/3.0/wine
104M	/opt/google/picasa/3.0
104M	/opt/google/picasa
104M	/opt/google
104M	/opt
du: cannot access `/proc/30405/task/30405/fd/3': No such file or directory
du: cannot access `/proc/30405/task/30405/fdinfo/3': No such file or directory
du: cannot access `/proc/30405/fd/3': No such file or directory
du: cannot access `/proc/30405/fdinfo/3': No such file or directory
100M	/lib/modules/2.6.31-21-generic/kernel
105M	/lib/modules/2.6.31-21-generic
110M	/lib/modules/2.6.32-22-generic/kernel
116M	/lib/modules/2.6.32-22-generic
110M	/lib/modules/2.6.32-21-generic/kernel
116M	/lib/modules/2.6.32-21-generic
104M	/lib/modules/2.6.28-17-generic/kernel
107M	/lib/modules/2.6.28-17-generic
444M	/lib/modules
493M	/lib
137M	/usr/share/icons
116M	/usr/share/fonts/truetype
140M	/usr/share/fonts
164M	/usr/share/doc
1348M	/usr/share
205M	/usr/bin
159M	/usr/lib/debug/usr/lib/xulrunner-1.9.2.3
159M	/usr/lib/debug/usr/lib
159M	/usr/lib/debug/usr
159M	/usr/lib/debug
228M	/usr/lib/openoffice/basis3.2/program
283M	/usr/lib/openoffice/basis3.2
285M	/usr/lib/openoffice
1744M	/usr/lib
167M	/usr/src
151M	/usr/lib32
3708M	/usr
652164M	/
sander@athlon64:~$ 


```

---

### Post by archkidd on 2010-06-21
Thank you.  I ran your command and what it showed me was that I had 13.5GB of files in var/backup.  When investigating backup programs I had inadvertently set Simple Backup to do a weekly backup.  However, that quantity does not show when I run Disk Usage Analyzer as that only shows  420MB in /var??  System Monitor does show my sda1/ drive as having 16.6GB in it which would match the 13.5GB in backup.  I now think my sda5/ is acting as my Home directory as System Monitor show 2.3GB and The Analyzer show 2.3 in /home.  As a newbie I am learning and not sure I really understand.  What I don't know now is how to find and delete the backups so that I can check this  (I do have other backups on a removable drive)

---

### Post by sanderj on 2010-06-21
Post the output of the one-line here.

And post the output of 'mount' here.

---

### Post by archkidd on 2010-06-21
Sory for the delay I had to go out.
The output was:
du: cannot access `/home/archie/.gvfs': Permission denied
du: cannot access `/proc/3281/task/3281/fd/4': No such file or directory
du: cannot access `/proc/3281/task/3281/fdinfo/4': No such file or directory
du: cannot access `/proc/3281/fd/4': No such file or directory
du: cannot access `/proc/3281/fdinfo/4': No such file or directory
172M    /lib/modules
215M    /lib
232M    /var/backup/2010-05-22_07.45.42.572838.archie-laptop.inc
388M    /var/backup/2010-05-09_07.53.57.450945.archie-laptop.ful
620M    /var/backup/2010-06-02_16.48.02.085561.archie-laptop.ful
424M    /var/backup/2010-05-17_07.58.49.238325.archie-laptop.ful
384M    /var/backup/2010-06-17_10.46.02.135264.archie-laptop.inc
5773M    /var/backup/2010-06-21_11.00.59.308887.archie-laptop.ful
212M    /var/backup/2010-06-16_11.13.04.462800.archie-laptop.inc
625M    /var/backup/2010-06-13_16.32.14.320699.archie-laptop.ful
600M    /var/backup/2010-05-25_10.26.09.139243.archie-laptop.ful
3098M    /var/backup/2010-06-18_12.34.51.417132.archie-laptop.inc
13562M    /var/backup
188M    /var/lib
177M    /var/cache/apt/archives
204M    /var/cache/apt
222M    /var/cache
13983M    /var
146M    /usr/bin
122M    /usr/share/icons
117M    /usr/share/doc
1047M    /usr/share
163M    /usr/src
169M    /usr/lib/openoffice/basis3.2/program
223M    /usr/lib/openoffice/basis3.2
225M    /usr/lib/openoffice
1100M    /usr/lib
2502M    /usr
18934M    /

What do you mean by the output of 'mount'?

---

### Post by sanderj on 2010-06-22
So, how about removing the two big directories:

```
5773M /var/backup/2010-06-21_11.00.59.308887.archie-laptop.ful
3098M /var/backup/2010-06-18_12.34.51.417132.archie-laptop.inc

```

Use file browser Nautilus to delete these two directories.
If that doesn't work (for example because you need to be root), use the command line:

```
sudo rm -rf /var/backup/2010-06-21_11.00.59.308887.archie-laptop.ful
```

---

### Post by archkidd on 2010-06-22
The command line worked.  I could not remove them using nautilus.  I can now remove the others by substituting in the command line and I have removed Simple Backup. so the problem should not recur.  Thank you so much.  Once again I have learned a lot more about Ubuntu and really appreciate the support that the whole community gives. Thanks again.

---

### Post by ibuclaw on 2010-06-22
> **archkidd said:**
> The command line worked.  I could not remove them using nautilus.  I can now remove the others by substituting in the command line and I have removed Simple Backup. so the problem should not recur.  Thank you so much.  Once again I have learned a lot more about Ubuntu and really appreciate the support that the whole community gives. Thanks again.

As you've removed the backup utility, as for the other files:
/var/backup/2010-05-09_07.53.57.450945.archie-laptop.ful
/var/backup/2010-05-17_07.58.49.238325.archie-laptop.ful
/var/backup/2010-05-22_07.45.42.572838.archie-laptop.inc
/var/backup/2010-05-25_10.26.09.139243.archie-laptop.ful
/var/backup/2010-06-02_16.48.02.085561.archie-laptop.ful
/var/backup/2010-06-13_16.32.14.320699.archie-laptop.ful
/var/backup/2010-06-16_11.13.04.462800.archie-laptop.inc
/var/backup/2010-06-17_10.46.02.135264.archie-laptop.inc
/var/backup/2010-06-18_12.34.51.417132.archie-laptop.inc
/var/backup/2010-06-21_11.00.59.308887.archie-laptop.ful

Wouldn't it be a good idea to remove the others too? Which the exception of the last one, being a full backup and all... As you never know. :)

---

### Post by archkidd on 2010-06-22
Yes, that is exactly what I am doing right now.  I need  to look for another backup program.  I use rsync to backup to an external usb drive but cannot find one that will allow me to backup to my network NAS drive.  Do you use one that does that?  I have searched the forums and posted the query but not had any luck. There must be one but Simple Backup for instance just will not recognize that my NAS drive is there even though I have mounted it and can drag files back and forward to/from it.

---

### Post by jerome1232 on 2010-06-22
Is it just me or are 98% of root partition full threads caused by simple backup!

---

### Post by archkidd on 2010-06-22
I was surprised to find the backup files there.  Why would a backup program put the files in root and not in home or better yet on a different drive altogether. I have always considered a main reason for the backup being to recover from a hard drive failure (other than operator error in deleting the wrong file :))

---

### Post by ibuclaw on 2010-06-22
> **archkidd said:**
> I was surprised to find the backup files there.  Why would a backup program put the files in root and not in home or better yet on a different drive altogether. I have always considered a main reason for the backup being to recover from a hard drive failure (other than operator error in deleting the wrong file :))

What you must try and consider is that some of the more power users will indeed have, /, /boot, /home, /usr and /var as separate filesystems or disks. :)

I believe Debian and Fedora offer this as a recommended option for advanced users, for instance.

---

### Post by archkidd on 2010-06-24
I can appreciate that.  I am not sure I understand why but that is OK, maybe when I get more experience.  But it would help newbies if the "**Simple**" Backup gave a little more advice on where the files are stored and warned of the danger of filling your root directory. Just a thought.  Meanwhile I have just deleted it and moved on.
Thanks

---

