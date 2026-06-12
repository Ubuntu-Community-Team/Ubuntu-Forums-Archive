---
title: "more about my full file"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by halbertinill on 2009-06-17
when i ran df -h, I got the following:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  2.8G  458M  87% /
varrun               1009M  104K 1009M   1% /var/run
varlock              1009M     0 1009M   0% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M     0 1009M   0% /dev/shm
lrm                  1009M  1.9M 1007M   1% /lib/modules/2.6.24-24-lpia/volatile
gvfs-fuse-daemon      3.4G  2.8G  458M  87% /home/pat/.gvfs

Do I have a situation where I have two copies of the OS here?  One as 
"/dev/sda2" and one as "gvfs-fuse-daemon"?

Then,when I run sudo du -sh /* I get this:
 sudo du -sh /*
[sudo] password for pat: 
4.9M    /bin
27M    /boot
0    /config-done
76K    /dev
12M    /etc
du: cannot access `/home/pat/.gvfs': Permission denied
43M    /home
4.0K    /initrd
0    /initrd.img
0    /initrd.img.old
183M    /lib
4.0K    /lost+found
4.0K    /media
4.0K    /mnt
118M    /opt
du: cannot access `/proc/10151/task/10151/fd/4': No such file or directory
du: cannot access `/proc/10151/task/10151/fdinfo/4': No such file or directory
du: cannot access `/proc/10151/fd/4': No such file or directory
du: cannot access `/proc/10151/fdinfo/4': No such file or directory
0    /proc
476K    /root
4.1M    /sbin
0    /squashmnt
4.0K    /srv
0    /sys
72K    /tmp
2.2G    /usr
227M    /var
0    /vmlinuz
0    /vmlinuz.old

can someone translate?

---

### Post by unutbu on 2009-06-17
halbertinill, I think everything looks fine.

~/.gvfs is the location where Gnome Virtual File Systems are mounted.
The files you see in there are virtual files. They act like regular files, but they don't (generally) exist on your hard drive. Samba filesystems get mounted there. Files in camera cards can also be mounted there. So don't worry about any numbers reported by df or du regarding gvfs -- it really isn't taking up any hard drive space. (The files in there do take up space on drives on other machines. But they get magically mounted in ~/.gvfs so they look like they are a part of your hard drive.)

This error message:
```

du: cannot access `/proc/10151/task/10151/fd/4': No such file or directory

```
is a manifestation of a "race condition". When the du command began, there was a process with PID number 10151. That process ended before du could sum up the size of /proc/10151.
When the process with PID number 10151 ended, the files in /proc/10151 were deleted. So du complains that the file /proc/10151/task/10151/fd/4 disappeared.

At least this is the way I think things work.
I'd be happy to hear if anyone can correct me on the facts.

---

### Post by Celauran on 2009-06-17
> **halbertinill said:**
> when i ran df -h, I got the following:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  2.8G  458M  87% /
```
can someone translate?
That's your problem right there. Your whole partition is only 3.4GB.

---

### Post by unutbu on 2009-06-17
Yep, I missed that. A 3.4GB root partition (including /home) would be uncomfortably tight.

---

### Post by halbertinill on 2009-06-17
Thanks, I'm not sure what to do about it.  This IS a mini netbook (dell) and the hardware is what it is.  Oh well.

---

### Post by Mornedhel on 2009-06-17
I'd suggest buying a 8-16 GB USB drive and keeping it in your pocket at all times. Just make sure you don't have any critical/sensitive/personal data on it, and then you can use the netbook's internal drive for the OS and applications only, and the external drive for your data.

---

