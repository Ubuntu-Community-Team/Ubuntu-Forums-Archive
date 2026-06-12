---
title: "[SOLVED] Understanding Device Files"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by azurepancake on 2009-01-06
For awhile now, I've been quite curious about these mysterious device files placed in my /dev/ directory. I've done a little reading about the device numbering system and how there are two numbers that represent a device. The major device number and the minor.

So I journeyed into my /dev/ directory and ran the following command:

```

tristan@panzerkunst:/dev$ ls -lah sda*
brw-rw---- 1 root disk **8, 0** 2009-01-01 18:44 sda
brw-rw---- 1 root disk **8, 1** 2009-01-01 18:45 sda1
brw-rw---- 1 root disk **8, 2** 2009-01-01 18:44 sda2
brw-rw---- 1 root disk **8, 5** 2009-01-01 18:44 sda5

```

My main system partitions are labeled as **sda**, and that is why I ran the above command. My drive is a SATA drive and I recall reading that sda is the device name given to SCSI drives as well, and that the minor device numbers for SCSI drivers ranges from 1 to 15.

So I am curious if this means that one could have up to 15 partitions on a SATA or SCSI drive at once, and no more with Linux? Or would it then continue to use a new naming convention? Or am I just completely lost? 

And also I am guessing that the major device channel 8 is used for both SATA and SCSI or just SATA?

Sorry if this seems like a unimportant question. I still consider my self quite the neophyte and I'd just like to develop a better understanding of this and will appreciate any ones knowledge.

Thanks for reading :)

---

### Post by Cypher on 2009-01-06
Devices in the /dev directory are conduits to drivers that are running in Kernel space. These special files allow user-level applications to safely talk to those drivers.

The major number must be unique for each deviecs that speak to a specific driver. The minor numbers have different meaning depending on what the driver author wanted them to be.

So in one instance I could create a driver that has 2 functions (say hello and say goodbye, for example), I would assign different minor numbers to the 2 functions, and thus 2 entries in the /dev directory. When a user used a particular file in /dev directory, based on the major and minor numbers, I know what they want me to do and the driver will perform the action.

In other instances, like the SCSI driver, the minor numbers represent the partitions on a given HD. The major number is reserved for driver identification.

There are a few major numbers that are reserved by the Linux Kernel and cannot be used by anyone else. Major numbers starting at 254 and decrementing down are available for anyone to use.

The [device.txt]("http://lxr.linux.no/linux+v2.6.28/Documentation/devices.txt") file in the Linux Kernel describes these reserved numbers.

---

### Post by azurepancake on 2009-01-07
Yap, that cleared it up for me. Thanks very much!

---

