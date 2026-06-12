---
title: "can't use my Swap partition"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Govind Gupta on 2010-08-09
PFB my output for 

cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=974211bb-c16e-48bc-b75d-06577c189a87 /               ext4    errors=remount-ro 0       1


i enabled the swap partition from gparted but it seems my System is not using this partition.

Its my first day with Linux !! :o

plz also let me know is there any way to use hibernate as used in Windows.

thanks

---

### Post by jtarin on 2010-08-09
try the command ```
fdisk -l /dev/sda
``` from the terminal...see if its listed. . Make sure you exit the terminal.

---

### Post by john newbuntu on 2010-08-09
Well, your fstab does not have an entry for the swap partition.  Typically, it should look like:```

UUID=2dabcd10a-122d-43aa-b336-f45cc844689f none  swap  sw  0 0
```where the long number after UUID= is the UUID corresponding to the swap partition obtained from the output of:
```
sudo blkid -c /dev/null
```Once you update this value in fstab, run the command:
```
sudo swapon -a
```Then check is swap is being used using either of these commands;
```
free -m 
swapon -s
```

---

