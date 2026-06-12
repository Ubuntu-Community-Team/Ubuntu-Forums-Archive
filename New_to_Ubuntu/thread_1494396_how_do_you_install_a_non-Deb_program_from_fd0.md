---
title: "how do you install a non-Deb program from fd0"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by harryliddic on 2010-05-26
I am forced to install a non .deb linux program from a floppy disk I know there is some changing of roots but don't know how. I program is GENESIS neural simulator and was in the Karmic repos but it not in Lucid. I have to resort to a disk in the back of the Book of genesis.

---

### Post by Ozymandias_117 on 2010-05-26
Can you post the output of ```
ls -l
``` wherever you have it mounted at?

---

### Post by harryliddic on 2010-05-26
Here it is
> harry@harry-desktop:~$ ls -l
total 36
drwxr-xr-x 5 harry harry 4096 2010-05-26 18:49 Desktop
drwxr-xr-x 2 harry harry 4096 2010-05-24 05:13 Documents
drwxr-xr-x 2 harry harry 4096 2010-05-20 03:22 Downloads
-rw-r--r-- 1 harry harry  179 2010-05-20 03:08 examples.desktop
drwxr-xr-x 2 harry harry 4096 2010-05-20 03:22 Music
drwxr-xr-x 3 harry harry 4096 2010-05-20 12:29 Pictures
drwxr-xr-x 2 harry harry 4096 2010-05-20 03:22 Public
drwxr-xr-x 2 harry harry 4096 2010-05-20 03:22 Templates
drwxr-xr-x 3 harry harry 4096 2010-05-21 02:32 Videos


---

### Post by Ozymandias_117 on 2010-05-26
I was meaning in the Floppy's directory :P I would guess it would be somewhere in /media or /mnt 

If you can't find it, after inserting the floppy post the results of ```
mount
```

---

### Post by harryliddic on 2010-05-26
I made an error it is sr0 not fd0
> /dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/harry/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=harry)
/dev/sr0 on /media/GENESIS 2.1 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


---

### Post by Ozymandias_117 on 2010-05-26
Please post the output of ```
ls -l /media/GENESIS\ 2.1
```

---

### Post by harryliddic on 2010-05-26
here it is 
> harry@harry-desktop:~$ ls -l /media/GENESIS\ 2.1
total 32
-rw-r--r--  1 harry harry 4464 1997-08-21 21:17 A-ReadMe.html
-rw-r--r--  1 harry harry 3291 1997-08-21 21:17 A-ReadMe.txt
drwxr-xr-x  3 harry harry 2048 1997-08-20 19:00 BABEL
-rw-r--r--  1 harry harry 3701 1997-08-21 20:50 Contents.html
-rw-r--r--  1 harry harry 2000 1997-08-20 18:09 Contents.txt
drwxr-xr-x  2 harry harry 2048 1997-10-02 21:55 Distributions
drwxr-xr-x 15 harry harry 4096 1997-08-20 21:21 genesis
drwxr-xr-x  2 harry harry 2048 1997-10-02 21:55 Install
-rw-r--r--  1 harry harry 2080 1997-08-20 18:15 LEGAL.txt
drwxr-xr-x 10 harry harry 2048 1997-08-12 01:10 pgenesis
drwxr-xr-x  4 harry harry 2048 1997-08-06 06:36 pvm3
-r--r--r--  1 harry harry  521 1997-10-03 01:19 TRANS.TBL
harry@harry-desktop:~$ 


---

### Post by Ozymandias_117 on 2010-05-26
```
ls -l /media/GENESIS\ 2.1/Install
```

You may want to look over that A-ReadMe.txt file too. It may help some.

---

### Post by harryliddic on 2010-05-26
here it is
> harry@harry-desktop:~$ ls -l /media/GENESIS\ 2.1/Install
total 17
-rwxr-xr-x 1 harry harry 2979 1997-08-12 01:59 bininstall
-rw-r--r-- 1 harry harry 5521 1997-10-02 21:43 HowTo-Install.html
-rw-r--r-- 1 harry harry 4307 1997-10-02 21:54 HowTo-Install.txt
-rwxr-xr-x 1 harry harry 2774 1997-08-12 01:11 PGENESIS_Install
-r--r--r-- 1 harry harry  213 1997-10-03 01:19 TRANS.TBL
harry@harry-desktop:~$ 


---

### Post by Ozymandias_117 on 2010-05-26
I would suggest reading that "/media/GENESIS\ 2.1/Install/HowTo-Install.txt" If you don't understand it, or have questions about it,  post back the question. If you don't understand it at all then you're going to need to post the output of ```
cat /media/GENESIS\ 2.1/Install/HowTo-Install.txt
```

---

### Post by harryliddic on 2010-05-26
On the file browser Install is not there nor are any of the items marked directories. I s there some sort of hidden file mojo going on. I have read the README that let me to a file in "src" describing how to compile the program but wouldn't I still be left with the changing it to .deb?

---

### Post by Ozymandias_117 on 2010-05-27
It doesn't HAVE to be a .deb. All that .deb does it make it easier to install programs, basically .deb just automates the process of installing a program.

I have no idea why you wouldn't be able to see the directories...

The general process for installing something from source is going to the src directory and using the commands ```
./configure
make
sudo make install
``` They don't always have a ./configure file, and you will have to manually install any dependencies.

---

### Post by harryliddic on 2010-05-27
Thanks for your help and I am going to try Dolphin to see if I can find those dirs.

---

