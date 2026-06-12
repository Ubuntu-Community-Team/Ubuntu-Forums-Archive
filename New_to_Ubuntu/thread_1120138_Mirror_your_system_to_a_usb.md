---
title: "Mirror your system to a usb"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by cornman on 2009-04-08
Is there any way to mirror your entire system to a usb flash drive?
i have 8.04 x64 os with / directory of 8gb and /home directory of 40 gb

is there any way i could mirror everything in the / directory to the 16 gb usb flash drive?

---

### Post by aysiu on 2009-04-08
You can use *rsync* for this: ```
rsync -av --exclude="/home/cornman" / /media/usbflash
```

---

### Post by ddrichardson on 2009-04-08
> **aysiu said:**
> You can use *rsync* for this: ```
rsync -av --exclude="/home/cornman" / /media/usbflash
```
Would that require rsync to put it back? Only wondering if the OP means creating images rather than mirrors.

---

### Post by aysiu on 2009-04-08
I don't think you can image *sans* the /home directory unless /home is on a separate partition.

---

### Post by ddrichardson on 2009-04-08
> **aysiu said:**
> I don't think you can image *sans* the /home directory unless /home is on a separate partition.
You can if you're imaging partitions.

---

### Post by cornman on 2009-04-09
how would you mirror a partition? does it change the setting if i only copy a few partition? would it boot normally?

---

### Post by juancarlospaco on 2009-04-10
**Remastersys **make an ISO of your running Ubuntu, 
and you can use "**USB Disk creator**" to put the ISO on your USB Thumb Drive, and **boot**.

---

### Post by ddrichardson on 2009-04-10
I assummed you were doing it to have a backup. I use a live cd with partimage installed and an external drive. Image the entire partition and if it goes wrong put this image back on.

---

### Post by cornman on 2009-04-13
remastersys does not work on x64 version,
any other solution?

---

### Post by Jakey_TheSnake on 2009-04-13
You can use gparted to copy a partition exactly, but it would include your home folder and documents, so unless you've used under 16gb of space total (unlikely) you'd have to back up to an external HDD. 

The partition(s) involved also have to be unmounted at the time, so you'd have to boot from a LiveCD/LiveUSB.

---

