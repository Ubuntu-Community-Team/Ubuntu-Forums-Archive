---
title: "external A drive"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by thelmaster on 2011-01-16
I have a Ubuntu Dell desktop with 10.10 installed and unlike my USB thumb drives, my computer is not able to find my external A drive.  Does this have to be mounted with the command line?

---

### Post by ggarron on 2011-01-16
I think you mean, your floppy disk?

It is A in windows.

but 

/dev/fd0 

for Linux, it should be mounted for you as soon as you insert a disk in the drive.

---

### Post by thelmaster on 2011-01-16
Yes, floppy drive.  When I insert a floppy disk, the light on the drive comes on, but nothing happens.  When I go to Computer, it is not listed.

---

### Post by TeoBigusGeekus on 2011-01-16
Assuming it is a usb device, does it show when you give 
```
lsusb
```
in terminal?

---

### Post by thelmaster on 2011-01-16
Additional info.  lsusb did list a floppy drive, and when I accessed Computer it was there also, but nothing happened when I tried to open it.  There are two things I failed to mention; since having this problem as described I reloaded the OS, and my floppy disks were made on a windows computer.

---

### Post by thelmaster on 2011-01-16
Additional info.  lsusb did list a floppy drive, and when I accessed Computer it was there also, but nothing happened when I tried to open it.  There are two things I failed to mention; since having this problem as described I reloaded the OS, and my floppy disks were made on a windows computer.

---

### Post by TeoBigusGeekus on 2011-01-16
Can you post us the output of 
```
sudo fdisk -l
```
(-L)

---

### Post by thelmaster on 2011-01-16
lsusb does list the drive.  I get different results when I go to Computer than I previously described.  The floppy icon is displayed but I still cannot open it.  That may be because since I last encountered this problem I have reloaded my OS.  I failed to mention also that my floppy disks contain windows files.

---

### Post by ggarron on 2011-01-17
It should work with windows files.
Try to mount the disk manually.
You may need to access with a root account, then you can change permissions to have access with your account.

---

### Post by ggarron on 2011-01-17
It should work with windows files.
Try to mount the disk manually.
You may need to access with a root account, then you can change permissions to have access with your account.

---

### Post by srs5694 on 2011-01-17
First, floppy disks aren't ordinarily partitioned, so fdisk is useless with them.

Try this:

```

sudo blkid /dev/fd0

```

This should identify the filesystem on the floppy disk. (I'm assuming Linux is using the device filename /dev/fd0 for it; however, as I've never used a USB floppy drive, I'm not entirely sure this is correct.)

You can also try something like this:

```

sudo mount /dev/fd0 /mnt

```

This should mount the floppy disk to /mnt. (It'll be accessible only to root unless you add more options; this is just a first step for diagnostic purposes.)

Post back with the results, including any output produced by those commands and observations about physical activity (lights on the drive or if you can hear the thing whirring to life).

---

