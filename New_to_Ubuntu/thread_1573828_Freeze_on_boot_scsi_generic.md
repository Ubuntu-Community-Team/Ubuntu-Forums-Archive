---
title: "Freeze on boot scsi generic"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Ventec on 2010-09-13
Hi all,

Kind of new to the installation of Ubuntu etc. and have hit a bit of a snag...

The installation went smoothly for the most part and when I finally got grub to boot the OS it seemed to work alright - however after restarting a few dozen times now I have determined I have some intermittent error...

The system 9/10 times will hang at the point shown in the attached image.

For the sake of thoroughness things that might be relevant:-

I have installed the most recently available version of Ubuntu

I have tried checking fstab/gdisk to make sure everything looks alright in that (got that idea from a similar error I found in another forum).

I have determined that so far I can boot into single user mode 100% of the time (although the error may still appear at some point) 

The drive has a guid partition table due to the 4tb partition I have installed ubuntu to

The 4tb of hdd space is provided in the form of a RAID 5 setup (actual raid not software based)


Any help would be greatly appreciated as I seem to just be running into brick walls no matter what I try to do (have been searching around for an answer for some time)

---

### Post by Golem XIV on 2010-09-13
I'd check SCSI termination to make sure both ends of the SCSI chain are properly terminated.  If the termination is not properly done it may cause this kind of behaviour.

Also check if the system has recognized properly the SCSI Interface card and if it has loaded the correct drivers 

```
lspci | grep scsi
```

---

