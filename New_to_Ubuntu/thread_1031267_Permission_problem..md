---
title: "Permission problem."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by supererki on 2009-01-05
Hello. I have a really bad situation and i don't know what to do.. File permission and owner data is missing in my /home/erki subdirectories..

erki@psytrance:~$ ls -la /home/erki/Videos/
ls: cannot access /home/erki/Videos/01082008.mp4: Permission denied
ls: cannot access /home/erki/Videos/26072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23092008.mp4: Permission denied
ls: cannot access /home/erki/Videos/04092008.mp4: Permission denied
ls: cannot access /home/erki/Videos/06072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/..: Permission denied
ls: cannot access /home/erki/Videos/.: Permission denied
ls: cannot access /home/erki/Videos/30062008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23082008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23082008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/23092008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/05072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/09072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/Video002.3gp: Permission denied
ls: cannot access /home/erki/Videos/30062008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/neno_peryk_valkirya_rules: Permission denied
ls: cannot access /home/erki/Videos/03112008.mp4: Permission denied
ls: cannot access /home/erki/Videos/Videos.cbr: Permission denied
ls: cannot access /home/erki/Videos/16082008.mp4: Permission denied
ls: cannot access /home/erki/Videos/05102008.mp4: Permission denied
ls: cannot access /home/erki/Videos/09072008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/01112008.mp4: Permission denied
total 0
d????????? ? ? ? ?                ? .
d????????? ? ? ? ?                ? ..
-????????? ? ? ? ?                ? 01082008.mp4
-????????? ? ? ? ?                ? 01112008.mp4
-????????? ? ? ? ?                ? 03112008.mp4
-????????? ? ? ? ?                ? 04092008.mp4
-????????? ? ? ? ?                ? 05072008.mp4
-????????? ? ? ? ?                ? 05102008.mp4
-????????? ? ? ? ?                ? 06072008.mp4
-????????? ? ? ? ?                ? 09072008(001).mp4
-????????? ? ? ? ?                ? 09072008.mp4
-????????? ? ? ? ?                ? 16082008.mp4
-????????? ? ? ? ?                ? 23072008.mp4
-????????? ? ? ? ?                ? 23082008(001).mp4
-????????? ? ? ? ?                ? 23082008.mp4
-????????? ? ? ? ?                ? 23092008(001).mp4
-????????? ? ? ? ?                ? 23092008.mp4
-????????? ? ? ? ?                ? 26072008.mp4
-????????? ? ? ? ?                ? 30062008(001).mp4
-????????? ? ? ? ?                ? 30062008.mp4
-????????? ? ? ? ?                ? neno_peryk_valkirya_rules
-????????? ? ? ? ?                ? Video002.3gp
-????????? ? ? ? ?                ? Videos.cbr
erki@psytrance:~$ 

------------------------------
And it's the same with every subdirectory under /home/erki/. In the same time /home/erki/ itself and all system folders are ok.


erki@psytrance:~$ ls -la /home/erki/ |more
total 6947684
drwxrwxrwx 109 erki erki       12288 2009-01-05 15:09 .
drwxr-xr-x   4 root root        4096 2009-01-03 01:59 ..
-rw-r--r--   1 erki erki       69714 2008-11-06 21:48 18-08-08_0955.jpg
-rw-r--r--   1 erki erki       60521 2008-11-06 21:51 24-10-08_1329.jpg
drw-r--r--   7 erki erki        4096 2008-11-19 00:36 3
-rw-r--r--   1 erki erki      336199 2008-10-11 18:01 87950-perfect_pushpin_k3.tar.gz
-rw-r--r--   1 erki erki      472333 2008-11-12 19:52 A81E98D7-2802-4FD6-85B4-EA2DBBD3ED54-1990-00009E5CC2B9ABFA.png
drwx------   2 erki erki        4096 2008-11-19 19:46 .AbiSuite
drwx------   3 erki erki        4096 2008-10-11 18:33 .adobe
-rw-r--r--   1 erki erki       78580 2008-11-08 22:34 aids2.jpg
drwx------   9 erki erki        4096 2008-11-10 19:06 .amsn
drw-r--r--   2 erki erki        4096 2008-10-25 14:40 amsn_received
drwx------   2 erki erki        4096 2009-01-02 20:09 .aptitude
-rw-r--r--   1 erki erki           0 2008-10-24 21:45 Auto.pll
drwxr-xr-x   3 erki erki        4096 2009-01-05 05:42 .avidemux
-rw-------   1 erki erki       12586 2009-01-05 14:45 .bash_history
-rw-r--r--   1 erki erki         220 2008-10-11 13:36 .bash_logout
-rw-r--r--   1 erki erki        2928 2008-10-11 13:36 .bashrc
drwxrwxrwx   4 erki erki        4096 2009-01-05 07:13 bla
-rw-r--r--   1 erki erki       11618 2008-11-26 14:38 blalba.png
-rw-r--r--   1 erki erki       67480 2008-11-25 23:12 bulimia.jpg
drwxr-xr-x   9 erki erki        4096 2008-11-27 22:39 .cache
drwxr-xr-x   5 erki erki        4096 2009-01-05 14:48 .cairo-dock
-rw-r--r--   1 erki erki      339208 2008-12-28 20:49 cassile
drwxr-xr-x   9 erki erki        4096 2008-11-11 23:01 .cedega
-rw-r--r--   1 erki erki        1149 2009-01-04 03:22 .cedegarc
-rw-r--r--   1 erki erki        7248 2008-11-07 19:58 .civclientrc
-rw-------   1 erki erki           0 2008-11-07 19:58 .civserver_history
-rw-r--r--   1 erki erki       92158 2008-11-08 22:38 comicweedweird2.png
drwx------   3 erki erki        4096 2008-10-12 12:35 .compiz
drwxr-xr-x  24 erki erki        4096 2008-12-09 00:50 .config
-rw-r--r--   1 erki erki         159 2008-10-14 13:33 .ctsim
-rw-r--r--   1 erki erki        7354 2008-10-20 20:24 cv
-rw-r--r--   1 erki erki       90627 2008-11-20 20:04 cv_nuditud.pdf
drwx------   3 erki erki        4096 2008-10-21 16:01 .dbus
drwxr-xr-x   5 erki erki        4096 2008-10-20 17:54 .dc++
-rw-r--r--   1 erki erki          56 2008-11-06 19:44 .DCOPserver_psytrance__0
lrwxrwxrwx   1 erki erki          35 2008-11-06 19:44 .DCOPserver_psytrance_:0 -> /home/erki/.DCOPserver_psytrance__0
-rw-r--r--   1 erki erki      103424 2008-11-18 23:15 Dear recruiter.doc
drw-r--r--   4 erki erki        4096 2009-01-05 07:05 Desktop
-rw-r--r--   1 erki erki          28 2008-10-12 19:59 .dmrc
drw-r--r--   2 erki erki        4096 2009-01-02 22:49 Documents
drwxr-xr-x   5 erki erki        4096 2008-11-07 02:23 .dosemu
drw-r--r--   3 erki erki        4096 2009-01-04 03:29 EA Games
drwxr-x---   2 erki erki        4096 2008-11-17 15:58 .easytag
drwxr-xr-x   6 erki erki        4096 2008-12-02 11:28 .Editra
-rw-r--r--   1 erki erki    44717184 2008-10-25 15:37 ej1.mp3
drw-r--r--  15 erki erki        4096 2008-10-11 14:41 elfutils-0.131
-rw-r--r--   1 erki erki     1412328 2008-10-11 14:34 elfutils_0.131.orig.tar.gz

-------------------------------------
I really don't know what do to with it.. I probably messed it up my self. i'm reading a book about administrating ubuntu server and i tried out all kinds of commands :) ....  i already tried chmod and chown, but no luck.

i'll post you dmesg or /var/log/messages if you need .. 

erki@psytrance:~$ uname -a
Linux psytrance 2.6.27-8-generic #1 SMP Thu Nov 6 17:33:54 UTC 2008 i686 GNU/Linux

please help.

Erki
[email]supererki@gmail.com[/email]

---

### Post by cmnorton on 2009-01-05
Enter this command at an X-term (command line).

sudo ls -l /home/erki/Videos

At least you'll know who owns them.

Then, sudo chown -R erki /home/erki/Videos

It isn't that there are no permissions; it's you are not allowed even to list the files.

Now look at the permissions and see if everything works.

---

### Post by supererki on 2009-01-05
thank you for your answer. unfortunatly it didnt solve it yet..

erki@psytrance:~$ sudo ls -l /home/erki/Videos
[sudo] password for erki: 
total 183980
-rw-r--r-- 1 erki erki  1506031 2008-08-01 20:23 01082008.mp4
-rw-r--r-- 1 erki erki  2047796 2008-11-01 01:35 01112008.mp4
-rw-r--r-- 1 erki erki  1573301 2008-11-03 12:01 03112008.mp4
-rw-r--r-- 1 erki erki  2542602 2008-09-04 18:08 04092008.mp4
-rw-r--r-- 1 erki erki  2675792 2008-07-05 14:14 05072008.mp4
-rw-r--r-- 1 erki erki  2954111 2008-10-05 07:10 05102008.mp4
-rw-r--r-- 1 erki erki   486222 2008-07-06 14:51 06072008.mp4
-rw-r--r-- 1 erki erki  2604238 2008-07-09 19:40 09072008(001).mp4
-rw-r--r-- 1 erki erki 20401758 2008-07-09 10:49 09072008.mp4
-rw-r--r-- 1 erki erki 14054913 2008-08-16 23:03 16082008.mp4
-rw-r--r-- 1 erki erki  1039271 2008-07-23 12:24 23072008.mp4
-rw-r--r-- 1 erki erki    79739 2008-08-23 10:19 23082008(001).mp4
-rw-r--r-- 1 erki erki  3205075 2008-08-23 08:26 23082008.mp4
-rw-r--r-- 1 erki erki  1291466 2008-09-23 16:06 23092008(001).mp4
-rw-r--r-- 1 erki erki  1647836 2008-09-23 16:05 23092008.mp4
-rw-r--r-- 1 erki erki  1844741 2008-07-26 04:32 26072008.mp4
-rw-r--r-- 1 erki erki  9393617 2008-06-30 09:23 30062008(001).mp4
-rw-r--r-- 1 erki erki  8331081 2008-06-30 09:20 30062008.mp4
-rw-r--r-- 1 erki erki 21776384 2009-01-05 06:02 neno_peryk_valkirya_rules
-rw-r--r-- 1 erki erki  6011151 2008-04-17 05:48 Video002.3gp
-rw-r--r-- 1 erki erki 82631044 2008-12-23 12:55 Videos.cbr
erki@psytrance:~$ sudo chown -R erki /home/erki/Videos
erki@psytrance:~$ ls -l /home/erki/Videos
ls: cannot access /home/erki/Videos/01082008.mp4: Permission denied
ls: cannot access /home/erki/Videos/26072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23092008.mp4: Permission denied
ls: cannot access /home/erki/Videos/04092008.mp4: Permission denied
ls: cannot access /home/erki/Videos/06072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/30062008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23082008.mp4: Permission denied
ls: cannot access /home/erki/Videos/23082008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/23092008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/05072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/09072008.mp4: Permission denied
ls: cannot access /home/erki/Videos/Video002.3gp: Permission denied
ls: cannot access /home/erki/Videos/30062008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/neno_peryk_valkirya_rules: Permission denied
ls: cannot access /home/erki/Videos/03112008.mp4: Permission denied
ls: cannot access /home/erki/Videos/Videos.cbr: Permission denied
ls: cannot access /home/erki/Videos/16082008.mp4: Permission denied
ls: cannot access /home/erki/Videos/05102008.mp4: Permission denied
ls: cannot access /home/erki/Videos/09072008(001).mp4: Permission denied
ls: cannot access /home/erki/Videos/01112008.mp4: Permission denied
total 0
-????????? ? ? ? ?                ? 01082008.mp4
-????????? ? ? ? ?                ? 01112008.mp4
-????????? ? ? ? ?                ? 03112008.mp4
-????????? ? ? ? ?                ? 04092008.mp4
-????????? ? ? ? ?                ? 05072008.mp4
-????????? ? ? ? ?                ? 05102008.mp4
-????????? ? ? ? ?                ? 06072008.mp4
-????????? ? ? ? ?                ? 09072008(001).mp4
-????????? ? ? ? ?                ? 09072008.mp4
-????????? ? ? ? ?                ? 16082008.mp4
-????????? ? ? ? ?                ? 23072008.mp4
-????????? ? ? ? ?                ? 23082008(001).mp4
-????????? ? ? ? ?                ? 23082008.mp4
-????????? ? ? ? ?                ? 23092008(001).mp4
-????????? ? ? ? ?                ? 23092008.mp4
-????????? ? ? ? ?                ? 26072008.mp4
-????????? ? ? ? ?                ? 30062008(001).mp4
-????????? ? ? ? ?                ? 30062008.mp4
-????????? ? ? ? ?                ? neno_peryk_valkirya_rules
-????????? ? ? ? ?                ? Video002.3gp
-????????? ? ? ? ?                ? Videos.cbr
erki@psytrance:~$

---

### Post by supererki on 2009-01-05
anybody?

---

### Post by unutbu on 2009-01-05
It looks like you can list the files when you use sudo, but you can't when acting as a normal user. Perhaps you could use 
```

gksu nautilus
```
To copy the files (as root) to a new directory, then delete the Videos directory (as root) and create a new Videos directory (as erki)
and the move and chown the files into the new directory.

However, if you'd like to explore what is wrong first,
please post the output:
```

mount
df /home/erki/Videos
lsattr -d /home/erki/Videos
lsattr /home/erki/Videos

```

---

### Post by supererki on 2009-01-05
erki@psytrance:~$ mount

/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)

/proc on /proc type proc (rw,noexec,nosuid,nodev)

sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)

varrun on /var/run type tmpfs (rw,nosuid,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

udev on /dev type tmpfs (rw,mode=0755)

tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)

devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)

fusectl on /sys/fs/fuse/connections type fusectl (rw)

lrm on /lib/modules/2.6.27-8-generic/volatile type tmpfs (rw,mode=755)

/dev/sda5 on /media/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

/dev/sda1 on /media/system type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

/dev/sdb1 on /media/FRISBY type vfat (rw)

gvfs-fuse-daemon on /home/erki/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=erki)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

erki@psytrance:~$ 



erki@psytrance:~$ df /home/erki/Videos

Filesystem           1K-blocks      Used Available Use% Mounted on

/dev/sda3            100004720  73220660  21744068  78% /

erki@psytrance:~$ 



erki@psytrance:~$ lsattr -d /home/erki/Videos

------------------- /home/erki/Videos

erki@psytrance:~$ 


erki@psytrance:~$ lsattr /home/erki/Videos

/home/erki/Videos/01082008.mp4: Permission denied

/home/erki/Videos/26072008.mp4: Permission denied

/home/erki/Videos/23092008.mp4: Permission denied

/home/erki/Videos/04092008.mp4: Permission denied

/home/erki/Videos/06072008.mp4: Permission denied

/home/erki/Videos/..: Permission denied

/home/erki/Videos/.: Permission denied

/home/erki/Videos/30062008.mp4: Permission denied

/home/erki/Videos/23072008.mp4: Permission denied

/home/erki/Videos/23082008.mp4: Permission denied

/home/erki/Videos/23082008(001).mp4: Permission denied

/home/erki/Videos/23092008(001).mp4: Permission denied

/home/erki/Videos/05072008.mp4: Permission denied

/home/erki/Videos/09072008.mp4: Permission denied

/home/erki/Videos/Video002.3gp: Permission denied

/home/erki/Videos/30062008(001).mp4: Permission denied

/home/erki/Videos/neno_peryk_valkirya_rules: Permission denied

/home/erki/Videos/03112008.mp4: Permission denied

/home/erki/Videos/Videos.cbr: Permission denied

/home/erki/Videos/16082008.mp4: Permission denied

/home/erki/Videos/05102008.mp4: Permission denied

/home/erki/Videos/09072008(001).mp4: Permission denied

/home/erki/Videos/01112008.mp4: Permission denied

erki@psytrance:~$ 




In morning i had some problems. I wasnt able to copy, paste, rename, view properties, drag/drop or anything with the files in my external usb hdd. later on i discovered that i was unable to do those things anywhere. and it said permission denied or smth. anyway, i needed to write a dvd urgently so i used sudo nautilus to gain permissions. 
anyway. later i decided to restart x and it solved this problem. i guess they are related.

---

### Post by supererki on 2009-01-05
erki@psytrance:~$ sudo lsattr /home/erki/Videos
[sudo] password for erki: 
------------------- /home/erki/Videos/01082008.mp4
------------------- /home/erki/Videos/26072008.mp4
------------------- /home/erki/Videos/23092008.mp4
------------------- /home/erki/Videos/04092008.mp4
------------------- /home/erki/Videos/06072008.mp4
------------------- /home/erki/Videos/30062008.mp4
------------------- /home/erki/Videos/23072008.mp4
------------------- /home/erki/Videos/23082008.mp4
------------------- /home/erki/Videos/23082008(001).mp4
------------------- /home/erki/Videos/23092008(001).mp4
------------------- /home/erki/Videos/05072008.mp4
------------------- /home/erki/Videos/09072008.mp4
------------------- /home/erki/Videos/Video002.3gp
------------------- /home/erki/Videos/30062008(001).mp4
------------------- /home/erki/Videos/neno_peryk_valkirya_rules
------------------- /home/erki/Videos/03112008.mp4
------------------- /home/erki/Videos/Videos.cbr
------------------- /home/erki/Videos/16082008.mp4
------------------- /home/erki/Videos/05102008.mp4
------------------- /home/erki/Videos/09072008(001).mp4
------------------- /home/erki/Videos/01112008.mp4
erki@psytrance:~$

---

### Post by unutbu on 2009-01-05
Hm. The output did not reveal the source of problem -- at least nothing I could see.
How about try this:
```

mkdir /home/erki/NewVideos
sudo cp -a /home/erki/Videos/* /home/erki/NewVideos
sudo chown $USER:$USER /home/erki/NewVideos
```

Can you access your files in /home/erki/NewVideos ?
If so, then perhaps you can delete the old directory with
```

sudo rm -rf /home/erki/Videos
```

---

### Post by supererki on 2009-01-05
Yes, thank you, i can access my files again. 

erki@psytrance:~$ mkdir /home/erki/NewVideos
erki@psytrance:~$ sudo cp -a /home/erki/Videos/* /home/erki/NewVideos
erki@psytrance:~$ sudo chown erki:erki /home/erki/NewVideos/
erki@psytrance:~$ ls -l /home/erki/NewVideos/
total 183980
-rw-r--r-- 1 erki erki  1506031 2008-08-01 20:23 01082008.mp4
-rw-r--r-- 1 erki erki  2047796 2008-11-01 01:35 01112008.mp4
-rw-r--r-- 1 erki erki  1573301 2008-11-03 12:01 03112008.mp4
-rw-r--r-- 1 erki erki  2542602 2008-09-04 18:08 04092008.mp4
-rw-r--r-- 1 erki erki  2675792 2008-07-05 14:14 05072008.mp4
-rw-r--r-- 1 erki erki  2954111 2008-10-05 07:10 05102008.mp4
-rw-r--r-- 1 erki erki   486222 2008-07-06 14:51 06072008.mp4
-rw-r--r-- 1 erki erki  2604238 2008-07-09 19:40 09072008(001).mp4
-rw-r--r-- 1 erki erki 20401758 2008-07-09 10:49 09072008.mp4
-rw-r--r-- 1 erki erki 14054913 2008-08-16 23:03 16082008.mp4
-rw-r--r-- 1 erki erki  1039271 2008-07-23 12:24 23072008.mp4
-rw-r--r-- 1 erki erki    79739 2008-08-23 10:19 23082008(001).mp4
-rw-r--r-- 1 erki erki  3205075 2008-08-23 08:26 23082008.mp4
-rw-r--r-- 1 erki erki  1291466 2008-09-23 16:06 23092008(001).mp4
-rw-r--r-- 1 erki erki  1647836 2008-09-23 16:05 23092008.mp4
-rw-r--r-- 1 erki erki  1844741 2008-07-26 04:32 26072008.mp4
-rw-r--r-- 1 erki erki  9393617 2008-06-30 09:23 30062008(001).mp4
-rw-r--r-- 1 erki erki  8331081 2008-06-30 09:20 30062008.mp4
-rw-r--r-- 1 erki erki 21776384 2009-01-05 06:02 neno_peryk_valkirya_rules
-rw-r--r-- 1 erki erki  6011151 2008-04-17 05:48 Video002.3gp
-rw-r--r-- 1 erki erki 82631044 2008-12-23 12:55 Videos.cbr
erki@psytrance:~$ 


But still, i wonder what caused it.

---

### Post by unutbu on 2009-01-05
You might see lots of question marks in the output of ls -l when the filesystem is corrupt. Maybe fsck'ing the partition would have fixed the problem, 
```

sudo e2fsck -vy /dev/sda3
```
but e2fsck comes with some risk since it changes the filesystem and sometimes deletes inodes. I don't know enough about e2fsck to guarantee you wouldn't lose data. That is why I suggested copying the data first. 

I'm glad it worked. :)

---

### Post by supererki on 2009-01-05
thanks mate

---

