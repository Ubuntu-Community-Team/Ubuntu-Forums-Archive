---
title: "Problems mounting. Please help!"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Øivind123 on 2009-01-12
so, trying to watch Simpsons from a USB stick on my new asus eee 901.
Then this message comes up: Unable to mount the volume. Details: must be superuser to use mount. Im not very skilled with computers and especcially not Ubuntu. If someone could give me a nice detailed explanation on what to do i will be very very gratefull. 
Thanks in advance:)
Regards Øivind

---

### Post by kapok on 2009-01-12
is you're account on that computer an administrator?

---

### Post by Øivind123 on 2009-01-12
yes.

---

### Post by MeURi on 2009-01-12
I'm not an expert on this aspect, but it could just be something related to your fstab.

This file contains information about where the devices (hard drives, optical units, and so on) have to be mounted on. See [here](https://help.ubuntu.com/community/Fstab) for more information.

As said there, you can add the option "user" (without the quotes) to your usb stick mount options, and see if it solves the problem.

Let us know if everything goes well, or not :-P

---

### Post by kapok on 2009-01-12
try:

> sudo mount *filesystem location*

here, filesystem location can be found by simply looking at where in your computer the usb is located. (probably ~/media/disk)

---

### Post by Øivind123 on 2009-01-12
So, there is no easy way to do this? cba reading through all that now. I find it alittle disturbing that i have to do alot of things i dont know a clue about just to watch some simpsons...

---

### Post by cariboo on 2009-01-12
Open an Apllications-->Accessories-->terminal to see what device_lable Linux assigns to your device. When you plug in your device in the terminal type:

```
dmesg | tail -n10 
```

This will print out the last 10 lines of dmesg. The output should look something like this:

```
 dmesg | tail -n10
[ 5764.225826] sd 6:0:0:0: [sdc] Write Protect is off
[ 5764.225829] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 5764.225831] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 5764.230447] sd 6:0:0:0: [sdc] 15663104 512-byte hardware sectors: (8.01 GB/7.46 GiB)
[ 5764.231815] sd 6:0:0:0: [sdc] Write Protect is off
[ 5764.231818] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 5764.231820] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 5764.231824]  sdc: sdc1
[ 5764.232824] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 5764.232892] sd 6:0:0:0: Attached scsi generic sg3 type 0
```

In the eighth line you will see sdc: sdc1. This is the device lable Linux assigns to my device. Your experience may differ. to mount you device in the same terminal type:

```
sudo mount /dev/sdc1 /mnt
```

The above command will ask you for your password, when you type your password it will not be echoed back. Your device should now be mounted in a directory called /mnt. Navigate to /mnt in Nuatilus : Places-->Home Folder-->Filesystem-->mnt.

You should now be able to watch your videos.

---

### Post by kapok on 2009-01-12
did it work?

---

### Post by Øivind123 on 2009-01-12
it says i dont got the file

oivind123@oivind123-laptop:~$ dmesg | tail -n10
[  217.047513] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[  217.047524]  sdc: sdc1
[  217.049383] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[  217.049487] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  217.049671] scsi 2:0:0:1: Attached scsi generic sg3 type 5
[  217.153118] Driver 'sr' needs updating - please use bus_type methods
[  217.160342] sr0: scsi3-mmc drive: 48x/48x tray
[  217.160357] Uniform CD-ROM driver Revision: 3.20
[  217.160523] sr 2:0:0:1: Attached scsi CD-ROM sr0
[  224.382156] usb 5-2: USB disconnect, address 4
oivind123@oivind123-laptop:~$ sudo mount /dev/sdc1 /mnt
[sudo] password for oivind123: 
mount: special device /dev/sdc1 does not exist
oivind123@oivind123-laptop:~$

---

### Post by Øivind123 on 2009-01-12
lol, it worked.
thanks alot =D

---

### Post by MeURi on 2009-01-14
You should mark the thread as solved, then ;-)

---

