---
title: "how do i format a drive to use as usb backup"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by Mtrboat on 2009-12-24
I have a BYTECC USB 2.0 Drive Mate and would like to use this to make a backup drive so i can clesn off all the old files like Music,Pictures And Videos. If anyone can help me with this i can keep my Laptop clean and fast.

---

### Post by juancarlospaco on 2009-12-24
**Right Click--->Format**
*On Ubuntu 9.10 Karmic*

---

### Post by nikhilbhardwaj on 2009-12-24
first you need to find out what is the name of this device assigned by ubuntu
to find out first unplug this usb device
and type
```

sudo fdisk -l

```
now plug this in and run the same command
you'll notice an additional entry
like /dev/sdc1 or sdb1 etc depending on the number of disks you have

lets say that your deive is /dev/sdc
replace sdc with whatever is the actual name and in the terminal run
```

sudo cfdisk /dev/sdc

```

now delete the existing partitions and create one primary linux partition which takes up the entire size
before quiting cfdisk make sure that you write the changes to the disk

at this point you may need to disconnect and reconnect your drive
i'm assuming you want to format to ext4
now finally run
```

sudo mkfs.ext4 /dev/sdc1

```

thats it you now have a formatted partition with ext4 for your backup

---

### Post by oldsoundguy on 2009-12-24
or you can save that terminal work and use gparted.

Just plug it in, launch gparted (called partition editor under your system>administration .. if not there, install it from Synaptic and leave it installed), go looking for the drive in the GUI, and format the thing.  Works for me and I have USB drives from 8gb thumbs to 500 gb wd's for data storage.

---

