---
title: "Out of memory"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by jauntybluefish on 2009-11-29
Hi,
I ran out of memory, but I have a large partition for home.
Can anyone advise me please.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.9G  6.9G     0 100% /
tmpfs                 438M     0  438M   0% /lib/init/rw
varrun                438M  108K  438M   1% /var/run
varlock               438M     0  438M   0% /var/lock
udev                  438M  156K  438M   1% /dev
tmpfs                 438M     0  438M   0% /dev/shm
lrm                   438M  2.2M  436M   1% /lib/modules/2.6.28-16-generic/volatile
/dev/sda7              35G  4.2G   30G  13% /home
overflow              1.0M   56K  968K   6% /tmp

Thanks
Andy

---

### Post by scragar on 2009-11-29
Hope you don't mind me asking, but what's using all that disk space?
```
ls -l /
```

---

### Post by jauntybluefish on 2009-11-29
Good question.
Here is the output.

total 84
drwxr-xr-x   2 root root  4096 2009-11-13 19:16 bin
drwxr-xr-x   3 root root  4096 2009-11-13 19:17 boot
lrwxrwxrwx   1 root root    11 2009-11-03 22:34 cdrom -> media/cdrom
drwxr-xr-x  16 root root  3840 2009-11-29 17:28 dev
drwxr-xr-x 147 root root 12288 2009-11-29 17:28 etc
drwxr-xr-x   4 root root  4096 2009-11-21 12:28 home
lrwxrwxrwx   1 root root    33 2009-11-04 00:05 initrd.img -> boot/initrd.img-2.6.28-16-generic
lrwxrwxrwx   1 root root    33 2009-11-03 22:48 initrd.img.old -> boot/initrd.img-2.6.28-11-generic
drwxr-xr-x  20 root root 12288 2009-11-23 13:12 lib
drwx------   2 root root 16384 2009-11-03 22:34 lost+found
drwxr-xr-x   5 root root  4096 2009-11-29 17:28 media
drwxr-xr-x   2 root root  4096 2009-04-13 10:33 mnt
dr-xr-xr-x 147 root root     0 2009-11-29 17:26 proc
drwx------  18 root root  4096 2009-11-26 16:29 root
drwxr-xr-x   2 root root  4096 2009-11-21 11:58 sbin
drwxr-xr-x   2 root root  4096 2009-03-06 16:21 selinux
drwxr-xr-x   2 root root  4096 2009-04-20 14:59 srv
drwxr-xr-x  12 root root     0 2009-11-29 17:26 sys
drwxrwxrwt  14 root root   360 2009-11-29 20:27 tmp
drwxr-xr-x  11 root root  4096 2009-04-20 15:00 usr
drwxr-xr-x  16 root root  4096 2009-11-21 12:30 var
lrwxrwxrwx   1 root root    30 2009-11-04 00:05 vmlinuz -> boot/vmlinuz-2.6.28-16-generic
lrwxrwxrwx   1 root root    30 2009-11-03 22:48 vmlinuz.old -> boot/vmlinuz-2.6.28-11-generic

I do not know what that means.
Any ideas?

Thanks 
Andy

---

### Post by mlentink on 2009-11-29
Even though you've got plenty of space for your documents, you do not have space left for your programs and temporary files.
Seeaing as how both your root and home partitions are on the same drive, the solution is simple:
Boot with the LiveCD
Make sure all partitions on your harddsik are unmounted
Using GParted, decrease the size of you home partition
Increase the size of your root partition ('/') to fill up the freeed up space.
reboot

---

### Post by scragar on 2009-11-29
> **mlentink said:**
> Even though you've got plenty of space for your documents, you do not have space left for your programs and temporary files.
Seeaing as how both your root and home partitions are on the same drive, the solution is simple:
Boot with the LiveCD
Make sure all partitions on your harddsik are unmounted
Using GParted, decrease the size of you home partition
Increase the size of your root partition ('/') to fill up the freeed up space.
reboot

You can't just do that, ubuntu uses UUIDs, these would change with the partitions being resized, meaning nothing will mount and he'll be smartly outputted to a busybox terminal with no idea what's going on or how to fix it.

My first piece of advice is to find out why he's using so much space on his install, when it should be large enough for most users needs.
Try running these commands, then see if the free space goes up by any noticeable amount
```
sudo apt-get clean
sudo rm /var/log/Xorg.{2,3,4}.log* /var/log/*.{2,3,4}
```
The first will clean the apt cache of packages you've downloaded and installed, the second will delete log files that aren't needed anymore.

---

### Post by jauntybluefish on 2009-11-29
Ok thanks guys.
The first command did nothing that I could see.
The second gave this output.

andy@computer:~$ sudo rm /var/log/Xorg.{2,3,4}.log* /var/log/*.{2,3,4}
rm: cannot remove `/var/log/Xorg.2.log*': No such file or directory
rm: cannot remove `/var/log/Xorg.3.log*': No such file or directory
rm: cannot remove `/var/log/Xorg.4.log*': No such file or directory
rm: cannot remove `/var/log/*.2': No such file or directory
rm: cannot remove `/var/log/*.3': No such file or directory
rm: cannot remove `/var/log/*.4': No such file or directory

Are we any wiser?

Cheers
Andy

---

### Post by SuperSonic4 on 2009-11-29
It could be your package cache. If you run ```
ls -Arsh /var/apt/cache > ~/cache.txt
``` and either paste the contents of cache.txt or upload the text file



ls - list
A - Show all except . and ..
r - recursive (show subfolders)
s - size
h - human readable (MB)

---

### Post by jauntybluefish on 2009-11-29
Thanks guys,
I found the problem in .local/share. Loads of backup files.

Readout is good now

andy@computer:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             6.9G  3.0G  3.6G  46% /
tmpfs                 438M     0  438M   0% /lib/init/rw
varrun                438M  112K  438M   1% /var/run
varlock               438M     0  438M   0% /var/lock
udev                  438M  156K  438M   1% /dev
tmpfs                 438M     0  438M   0% /dev/shm
lrm                   438M  2.2M  436M   1% /lib/modules/2.6.28-16-generic/volatile
/dev/sda7              35G  4.2G   30G  13% /home


Cheers
Andy

---

### Post by XCan on 2009-11-29
I would have started with the disk usage analyzer tbh before issueing all those cleaning commands. But anyway good thing it worked out, 3 GB is a more reasonable size. :)

---

