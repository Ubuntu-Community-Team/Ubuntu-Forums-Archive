---
title: "Cant change ownership of harddrive"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by degarb on 2010-02-19
I attached a external usb hd   and 
sudo mkfs -t ext3 /dev/sdb


then  I cannot read or write to drive since it is root.   I don't understand why everyone cannot write to new drive.  it is folders that should have permissions not drives.

so, is ran 

sudo chown degarb:degarb /dev/sdb



but is still the root and I have no ability to do anything on the drive

---

### Post by 416inversed on 2010-02-19
I had a similar issue recently. I ran Nautilus as Root (in terminal)```
gksu nautilus
``` Navigating to the drive, right clicking to Properties>Permissions where I changed the ownership.

---

### Post by degarb on 2010-02-19
g.raphical k. s.uper u.ser

what does the k stand for?

---

### Post by 416inversed on 2010-02-19
> **degarb said:**
> g.raphical k. s.uper u.ser

what does the k stand for?
  Good question. I don't think I ever pondered that before. 

Doing a tad of googling, gives a kind of convoluted answer.

GKSU is the Super User front-end of GTK, which stands for GIMP Tool Kit, GIMP of course being GNU Image Manipulation Program, and GNU being the recursive GNU is Not Unix.

But yeah... I use GKSU as basically a Graphical sudo.

Perhaps others more well versed can clarify.

---

### Post by trikster_x on 2010-02-19
try typing:

```
sudo chown -R user:user /dev/sdb"x"
```

where "x" is the number of the partition on the device you want to change permissions for.  you may need to substitute /dev/sdb for the mount location of the partition on the disk in your file system.

---

### Post by Miljet on 2010-02-19
I think you might be attacking this from the wrong end. It is not ownership of the drive that is causing you problems, but ownership of the mount point where the drive is mounted. As a simple test, create a mount point in your home directory, without using sudo, and try mounting the drive there. If that works, you can either play with changing ownership of the regular mount point or with the settings in /etc/fstab.

---

