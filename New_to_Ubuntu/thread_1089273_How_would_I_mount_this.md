---
title: "How would I mount this ?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by mistypotato on 2009-03-06
Welcome to my question :D

I have a partition that I need to mount.....(/dev/sda3)

**fdisk -l**
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       35631   259987927+   5  Extended
**[COLOR="Red"]/dev/sda3           35632       38913    26362665   83  Linux[/COLOR]**
/dev/sda5            3265       16319   104864256    7  HPFS/NTFS
/dev/sda6           16320       16441      979933+  83  Linux
/dev/sda7           16442       35266   151211781   83  Linux
/dev/sda8           35267       35631     2931831   82  Linux swap / Solaris


**df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             142G  8.6G  127G   7% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  196K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G  404K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             942M   41M  854M   5% /boot



How would I mount /dev/sda3...
1). Temporarily
2). Permanently

thx

---

### Post by spcwingo on 2009-03-06
1) sudo mount /dev/sda3 /media/disk
2) check out this link:
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by mistypotato on 2009-03-07
That's what I thought but that returns..........

**[COLOR="Red"]mount: mount point /media/disk does not exist [/COLOR]** :(

---

### Post by mistypotato on 2009-03-07
> **spcwingo said:**
> 1) sudo mount /dev/sda3 /media/disk
2) check out this link:
[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")


Hello spcwingo,
That tutorial doesn't seem to cover my particular situation?
> **[COLOR="DarkOrange"]Warning[/COLOR]**: The tutorial on this page is for an internal drive that will serve as an extra data partition. If you would like to mount a separate drive or partition as /home instead, you want a different tutorial. 

The "different tutorial" was entitled......
**Create a separate home partition in Ubuntu**

I'm actually trying to mount an existing partition on the same hard drive as the root and home system.

---

### Post by ratmandall on 2009-03-07
> **mistypotato said:**
> That's what I thought but that returns..........

**[COLOR="Red"]mount: mount point /media/disk does not exist [/COLOR]** :(

```
cd /media/
sudo mkdir disk
```

---

