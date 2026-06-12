---
title: "NFS : trouble mounting"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by Fredvs79 on 2008-10-15
I'm trying to mount a network drive, but can't. 

fred@600m-laptop:/media/OneTouch4 Plus$ sudo mount 192.168.1.134 /mnt
                 mount: mount point /mnt does not exist

fred@600m-laptop:/media/OneTouch4 Plus$ sudo mkdir /mnt
                 mkdir: cannot create directory `/mnt': File exists

fred@600m-laptop:/media/OneTouch4 Plus$ ls -l / | grep mnt
                 ls: cannot access /mnt: Permission denied
                 d?????????   ? ?    ?        ?                ? mnt

fred@600m-laptop:/media/OneTouch4 Plus$ sudo rm -rf /mnt
                 rm: cannot remove `/mnt': Permission denied

fred@600m-laptop:/media/OneTouch4 Plus$ sudo rmdir /mnt
                 rmdir: failed to remove `/mnt': Device or resource busy

fred@600m-laptop:/media/OneTouch4 Plus$ sudo /etc/init.d/portmap stop
                 * Stopping portmap daemon...                [ OK ] 

fred@600m-laptop:/media/OneTouch4 Plus$ sudo /etc/init.d/nfs-kernel-server stop
                 * Stopping NFS kernel daemon                [ OK ] 
                 * Unexporting directories for NFS kernel daemon...[ OK ] 

fred@600m-laptop:/media/OneTouch4 Plus$ ps -ef | grep mnt
                fred       782 32252  0 14:35 pts/0    00:00:00 grep mnt

     Seems like nothing is using /mnt, but I still can't remove it, and I still can't mount to it because mount doesn't see it.
     Suggestions? any ideas?

---

### Post by penguinpi.com on 2008-10-16
First thing i noticed. When mounting a nfs share you need to specify the full path of the exported directory.

You wrote:  mount 192.168.1.134 /mnt

This needs to be more like ~# mount 192.168.1.134:/path/to/exports /mnt

(if this doesn't help)

the mount command shows currently mounted filesystems

~# mount

if something is mounted in /mnt

~# umount /mnt

or try

~# mount -a



Hope this Helps!

---

### Post by Fredvs79 on 2008-10-17
still having problems,

I've tried 

sudo mount 192.168.1.134:share /mnt

and I still get the error.
Nothing is mounted in /mnt currently

---

### Post by Fredvs79 on 2008-10-17
SOLVED!


It needs to be of the form

$ sudo mount host:path path

In my case it was
$ sudo mount 192.168.1.134:/share /mnt

(I was missing the :/share)

---

