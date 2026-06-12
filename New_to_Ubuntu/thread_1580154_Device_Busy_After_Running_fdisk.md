---
title: "Device Busy After Running fdisk"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by ajphall on 2010-09-22
Hi,
I'm not sure if this is the right section to post in, but I am new to Linux, so I thought I would start here!
I have a system with two hard drives, sda and sdb.
Ubuntu Server 10.04 is installed on sda
When I try to run fdisk on sdb to create a primary partition at sdb1, and write the changes to the partition table, it says that the table is updated, and I receive the message 

```
calling ioctl to re-read partition table
``` (I'm not sure if this is normal or not)

After this I am trying to make an ext3 file system on the newly created sdb1 with 

```
mkfs.ext3 /dev/sdb1
```and I receive the error 

```
/dev/sdb1 is apparently in use by the system: will not make a filesystem here!
```My solution to this is to reboot the computer, and try again to mkfs.ext3 /dev/sdb1, however, once this is done I get the error:

```
The device apparently does not exist; did you specify it correctly?
```I have no idea what to do.  I searched for hours to find a solution, and although other people are having similar problems, in general it is because the device is mounted, mine is not mounted, if I run umount I get a not found or device not mounted response.

Any help would be greatly appreciated,
Thanks,
Andrew

---

### Post by CharlesA on 2010-09-22
Is it mounted?

Try running this:

```
sudo lsof /dev/sdb1
```

---

### Post by myolbug on 2010-09-22
I can't offer help, but I want to say welcome to the forum!!!

---

### Post by ajphall on 2010-09-23
Thanks for the replies!
I tried lsof, and it doesn't return anything.
The drive is not mounted.
My (uneducated) guess is that fdisk is not finishing writing a new partition table, and therefore not releasing the disk properly.  This would explain to me why it is busy after running fdisk, and then once the computer is rebooted why the partition doesn't appear to exist.  Is this at all possible?  Is there any way to check this?  I have tried running ```
fuser /dev/sdb1
``` but this doesn't return anything.

Thanks for your help.

---

### Post by maclover on 2010-09-30
ok so since im new to liunx as well i dont really know where fdisk was placed at or is it called a different name???:? so plz help me since im having a smiler issue

---

