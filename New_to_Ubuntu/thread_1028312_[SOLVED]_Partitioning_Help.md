---
title: "[SOLVED] Partitioning Help"
date: 2009-01-02
forum: New to Ubuntu
---

### Post by intense.ego on 2009-01-02
With regards to [this issue]("http://ubuntuforums.org/showthread.php?t=1027065"), I decided to reinstall Ubuntu. I had a windows partition that I had not once used in the 2 years I've had ubuntu so I decided this was a perfect time to delete it and use the new available space to make my /home bigger.

I deleted the partition, but I could not add it to /home because the windows partition was /dev/sda1 and /home was /dev/sda4. Between them was /dev/sda2 - my /root partition(/dev/sda3 is extended and appears at the bottom of gparted). So I decided to allocate the available space to /dev/sda2 and then de-allocate it, and then allocate it to /dev/sda4 (I had done this before a few months back when I tried making room to install arch). 

I left the operation of enlarging /dev/sda2 on as I ate lunch, but when I returned I found that there was an error - something about block size not being able to be read. I decided to just try it again and see what happened, but when I did, I was told /dev/sda2 no longer exists and:

```
The kernel is unable to re-read the partitiontables on the following devices:
- /dev/sda
```

So now it doesn't seem like I can carry out any operations. What do I do? Should I just nuke the whole hard drive and start afresh? (I have removed all important files already)

---

### Post by taurus on 2009-01-02
What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by intense.ego on 2009-01-03
The output of that command was:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfc18b9a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1         906     7269412+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            6889        7296     3277260    5  Extended
/dev/sda4            1669        6888    41929650   83  Linux
/dev/sda5            7149        7296     1188778+  82  Linux swap / Solaris
/dev/sda6            6890        7148     2080386   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.3G   16M  1.3G   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 1.3G   16M  1.3G   2% /lib/modules/2.6.24-16-generic/volatile
varrun                1.3G  104K  1.3G   1% /var/run
varlock               1.3G     0  1.3G   0% /var/lock
udev                  1.3G   68K  1.3G   1% /dev
devshm                1.3G     0  1.3G   0% /dev/shm
tmpfs                 1.3G   12K  1.3G   1% /tmp
ubuntu@ubuntu:~$ 

```

I'm writing this right now from a live session, if that makes any difference to the output of the command.

---

### Post by gn2 on 2009-01-04
> **intense.ego said:**
> Should I just nuke the whole hard drive and start afresh? (I have removed all important files already)

Yes, just go for it.

Will save you wasting time fiddling about.

---

### Post by Michael.Godawski on 2009-01-04
I would also wipe the drive and do a fresh install.

If the errors keep occurring there might be a bad block, or some other hardware related problem.

---

