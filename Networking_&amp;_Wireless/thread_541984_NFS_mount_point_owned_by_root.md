---
title: "NFS mount point owned by root"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by k0maru on 2007-09-03
Greetings friends,

So, i setup NFS on our server (Gutsy) for our two laptops (both Fiesty). Things work well but for one thing: when i mount the nfs shares (as my usual user, or even on boot), the mountpoint gets owned by root. The problem is, i cannot make files in the top-level directory of the share. Here's the relevant bits of /etc/fstab

madhatter:/teaparty/alice       /media/alice            nfs     rw,user         0       0
madhatter:/teaparty/dormouse    /media/dormouse         nfs     rw,user         0       0
madhatter:/teaparty/marchhare   /media/marchhare        nfs     rw,user         0       0

and mount's output:

madhatter:/teaparty/alice on /media/alice type nfs (rw,noexec,nosuid,nodev,addr=192.168.11.199,user=iwakura)
madhatter:/teaparty/dormouse on /media/dormouse type nfs (rw,noexec,nosuid,nodev,addr=192.168.11.199,user=iwakura)
madhatter:/teaparty/marchhare on /media/marchhare type nfs (rw,noexec,nosuid,nodev,addr=192.168.11.199,user=iwakura)

and the perms, before and after mount:

drwxr-xr-x 2 iwakura root 4096 2007-09-04 01:06 alice
lrwxrwxrwx 1 root    root    6 2007-07-06 23:53 cdrom -> cdrom0
drwxr-xr-x 2 root    root 4096 2007-07-06 23:53 cdrom0
drwxr-xr-x 2 iwakura root 4096 2007-09-04 01:06 dormouse
drwxr-xr-x 2 iwakura root 4096 2007-09-04 01:06 marchhare


drwxr-xr-x 13 root root 4096 2007-09-03 00:41 alice
lrwxrwxrwx  1 root root    6 2007-07-06 23:53 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-07-06 23:53 cdrom0
drwxr-xr-x 11 root root 4096 2007-09-02 00:46 dormouse
drwxr-xr-x  5 root root 4096 2007-09-04 00:07 marchhare

Now, it strikes me that if i were mounting our home directories, this would be a real problem - so i must be doing something wrong. Anybody see what it is?

Kind thanks!
// k0maru

---

### Post by k0maru on 2007-09-04
Hi, reply to my own thread. The problem was permissions on the NFS server - root owned those directories being mounted.

A little chown solved everything.

later...

---

