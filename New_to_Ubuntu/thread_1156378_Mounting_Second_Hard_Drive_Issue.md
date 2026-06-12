---
title: "Mounting Second Hard Drive Issue"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by alberto.the.peguin on 2009-05-11
Hi,

I installed xubuntu 9.04 to my main HD and I'm trying to mount the slave. I looked through the documentation and used the following code:

```
sudo mount /dev/sdb /mnt
```It then asked for me to specify my filesystem type, which was in the documentation and I followed again with this:

```
sudo mount /dev/sdb /mnt  -t ext3
```This gave me the error:

> mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
I know the file system is correct because I just formated it through GParted and triple checked it. Why is this error coming up?

---

### Post by michy99 on 2009-05-11
Should it perhaps be /dev/sdb0 instead of /dev/sdb?

---

### Post by Bölvaður on 2009-05-11
you probably want it to automatically mounted at startup, not every time you turn on your pc.

First we make a place to mount it to.
Open the terminal (applications &#8594; accessories &#8594; terminal)
and make the new directory called newPartition... you can change the name (note that you are asked for password but the blinking thingy doesnt move... it is ok just type your password and press enter)
```
sudo mkdir /mnt/newPartition
```now we want to make it automatically be mounted at each boot
type in the terminal (paste in the terminal is ctrl+shift+v)
```
gksu gedit /etc/fstab
```add this line at the end of the file

/dev/sdb0            /mnt/newPartition       ext3    relatime        0       2

Alternativly you might want to copy the UUID of the partition instead of the logical name. you try to figure out which one is the correct one, it is located in /dev/disk/by-uuid

if you want to find the UUID you have to use the elimination method to find out which one is the one you want (the other's are probably already in fstab)
to open file manager at this location enter this command (alt+f2 if you have closed the terminal by now)
```
nautilus /dev/disk/by-uuid
```
the line you paste into fstab will look like this then

UUID=4b41b7d4-c3df-4d73-8694-5ae5692562ee           /mnt/newPartition            ext3    relatime        0       2

---

### Post by Miljet on 2009-05-11
You can find out the UUID by opening a terminal and typing

```
sudo blkid
```

---

### Post by alberto.the.peguin on 2009-05-11
i created a folder in /mnt to mount the drive on (/mnt/slave) and i also found the UUID for it. but i am unable to open up /etc/fstab and edit it. when i do actually go to the file and open it, it says it wont let me save. what do i do with it now?

also, i mounted the drive using the following code:

> sudo mount /dev/sdb1 /mnt/slave -t ext3

but im still unable to view it. the only thing in the /mnt/slave folder is a folder called "lost+found"

thanks for the help so far, but i still havent found a solution.

---

### Post by taurus on 2009-05-11
If /dev/sdb1 is a clean drive, then there should not be anything on it except the lost+found directory. 

And if you want to edit /etc/fstab with root privilege, you need to run

```
gksudo gedit /etc/fstab
```

---

### Post by orange-wedge on 2009-05-11
run the following to determine the physical partition labels:

[HTML]sudo fdisk -l[/HTML]

---

