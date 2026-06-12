---
title: "trouble with partition permissions and other HD ?s"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by sausages on 2009-01-02
I feel like this thread has been brought up many times, but I have scanned the forums and google and have yet to find a solution. 
  My HD is partitioned, using the ext3 format and gparted. I am having the problem of not being able to write to my partitions. I have tried several variations of chown commands but I always get the error "no such file or directory." I have tried mounting the volume and using /desktop/volumename as the location, it can't find it. 
  when I did ls -la /media the line for the partition read: drwxr-xr-x 3 root root 4096 2008-12-31 22:22 volumename.
  I am pretty new at this so any detailed instructions would be appreciated. 
I also have 2 swap partitions, I would like to eliminate one and create 1 bigger one, is this dangerous? Or will Ubuntu know which one to use automatically.
  i really don't understand how to use gparted, because even if I have unallocated space it won't let me increase the size of other partitions. Is there something I have to do first?

Thanks

---

### Post by logos34 on 2009-01-02
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(-->bottom, chown and chmod section)

swap:

sudo swapoff -a

or right-click on it in GParted.  Delete and resize.

sudo blkid

find the new swap UUID and replace old one in fstab:

sudo gedit /etc/fstab

sudo swapon -a

---

