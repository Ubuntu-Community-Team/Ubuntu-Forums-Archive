---
title: "change partition"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by webwiller on 2011-05-01
Hi guys!
During installation of new ubuntu I named a partition under /dos because it didnt allow me to put another name. Now I want my /dos partition to become /mnt/data.
Could you please tell me how to sort this out?
TY!!;)

---

### Post by mshahn on 2011-05-01
You may want to post your fstab.

cat /etc/fstab

---

### Post by webwiller on 2011-05-01
here is it:

>  webwiller@webwiller-HP-Compaq-6730s:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=45c5b4eb-df97-4619-b987-bb6bc24e2073 /               ext4    errors=remount-ro 0       1
# /dos was on /dev/sda6 during installation
UUID=7AA2CD1D03E8C88F /dos            ntfs    defaults,umask=007,gid=46 0       0
# /windows was on /dev/sda1 during installation
UUID=0274BA2700C04304 /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=e93ea611-9604-42e5-951d-2545496bfc60 none            swap    sw              0       0
 

---

### Post by mshahn on 2011-05-01
Seems like you would want to do the following:

mkdir /mnt/data
umount /dos

Then change this line:
UUID=7AA2CD1D03E8C88F /dos            ntfs    defaults,umask=007,gid=46 0       0

To this:
UUID=7AA2CD1D03E8C88F /mnt/data            ntfs    defaults,umask=007,gid=46 0       0

Finally:
mount /mnt/data

---

### Post by webwiller on 2011-05-01
> **mshahn said:**
> Seems like you would want to do the following:

mkdir /mnt/data
umount /dos

Then change this line:
UUID=7AA2CD1D03E8C88F /dos            ntfs    defaults,umask=007,gid=46 0       0

To this:
UUID=7AA2CD1D03E8C88F /mnt/data            ntfs    defaults,umask=007,gid=46 0       0

Finally:
mount /mnt/data

how do I change that line?
how do I edit that document(fstab)?

---

### Post by mshahn on 2011-05-01
Probably the most straight forward was is to do this:

# make a backup
sudo cp /etc/fstab /etc/fstab.bak

# open in gedit
sudo gedit /etc/fstab

# change /dos to /mnt/data

---

