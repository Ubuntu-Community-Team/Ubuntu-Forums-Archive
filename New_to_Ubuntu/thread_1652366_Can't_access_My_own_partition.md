---
title: "Can't access My own partition"
date: 2010-12-24
forum: New to Ubuntu
---

### Post by bj218 on 2010-12-24
Today I tried to access 1 of my own partitions ie "miscu" but am not allowed
see attached picture!! What could I have done to cause this? Also how do I 
remove this problem?

---

### Post by sandyd on 2010-12-24
> **bj218 said:**
> Today I tried to access 1 of my own partitions ie "miscu" but am not allowed
see attached picture!! What could I have done to cause this? Also how do I 
remove this problem?
wrong syntax. that wont work unless you have a corresponding entry in /etc/fstab


```

sudo mount [device] [full path]

```block device refers to the device column of the output of fstab
it should be something like "/dev/sda1" or "/dev/sda2" or "/dev/sdb2"

you can find the device by running 
```

sudo fdisk -l
```For example, if my device was /dev/sda1, and i wanted to mount it to /mnt, then
```

sudo mount /dev/sda1 /mnt
```

---

### Post by garvinrick4 on 2010-12-24
Just to continue post 2: If you want to mount to desktop you need a directory:
```
sudo mkdir /media/anything
``````
sudo mount /dev/sda1 /media/anthing
```Can see on desktop and will be in file sytem under /media. 
Post 2 will be in filesystem under /mnt
always unmount
```
sudo umount /mnt
```or
```
sudo umount /media/anything
```Have a Merry Christmas

---

### Post by |Eric| on 2010-12-24
do a  
```
blkid
```
you need to find witch partition you are trying to mount this gives you 
witch UUID is equal to what partition (miscu dosent mean anything) 
```
cat /etc/fstab 
```
will give your current fstab file 

and finaly 
fdisk -l will list your drives and their partitions 


you can then edit fstab to have the correct UUID and mountpoint \

note a normal user cannot mount drives you have to be root to do that (usually) 

also make sure that you have rw access to the folder ( has its not overiden on the mount command) 

most likely your trying to mount as regular user. 

you can use sudo to execute commands as root .

---

