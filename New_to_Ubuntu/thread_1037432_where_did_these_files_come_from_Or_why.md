---
title: "where did these files come from? Or why?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by adamogardner on 2009-01-11
under places I have things called 12.3 gb media, and 156.4GB media.  the 12.3 when I opened it looks like my file system - bin, boot, etc, and the like.  The other one looks like something else but similar.  I don't have any memory devices plugged in or anything.  So what are these?

---

### Post by whoop on 2009-01-11
usb mass storage devices
partitions on your harddisk(s)

---

### Post by teh_yodeler on 2009-01-11
What do you think they are?

---

### Post by mjheagle8 on 2009-01-11
do you have your hard drive partitioned? have you previously installed another distro?

---

### Post by Frak on 2009-01-11
It sounds like you have more than one filesystem mounted. Also, do you have any portable devices (removable hard drives, usb, etc.) inserted?

---

### Post by jemate18 on 2009-01-11
what is the output of

> df -h

or 
> less /etc/fstab

---

### Post by Captain_tux on 2009-01-11
Those are file systems outside of Ubuntu.

Are you dual-booting? Or have partitions outside of the current instance of Ubuntu?

---

### Post by mkvnmtr on 2009-01-11
The other partitions on my hard drive show like that whether they are mounted or not. Any external disks or partitions on disks show like that.

---

### Post by Joeb454 on 2009-01-11
Slightly off-topic, but if one of those is a Windows dual boot, then boot into Windows and go into My Computer, rename the C drive (essentially, this gives it a label).

When you reboot into Ubuntu, it'll read whatever you named the C drive to, and list it as that under the Places menu.

This helps me distinguish between my drives :)

---

### Post by adamogardner on 2009-01-11
> **jemate18 said:**
> what is the output of



or

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b268eb6a-59da-462c-a80d-897b34edbf38 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e09aa5d7-882f-481e-b7cb-c5bf1a8f5f25 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
## usbfs is the USB group in fstab file:
none /proc/bus/usb usbfs devgid=120,devmode=664 0 0
(END) 

adamogardner@CRONUS:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              71G   28G   40G  42% /
varrun                1.5G  140K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G   56K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-19-generic/volatile
/dev/scd0             1.1G  1.1G     0 100% /media/cdrom0
/dev/sda4              12G  1.9G  8.9G  17% /media/disk
/dev/sda1             146G   60G   87G  41% /media/disk-1
adamogardner@CRONUS:~$ less /etc/fstab
adamogardner@CRONUS:~$ 


I don't have any memory sticks or anything like that in my computer.

---

### Post by adamogardner on 2009-01-11
> **Captain_tux said:**
> Those are file systems outside of Ubuntu.

Are you dual-booting? Or have partitions outside of the current instance of Ubuntu?


Yes I dual boot from GRUB but this stuff just appeared somewhat recently.  and I'm not plugged into anything externally that I know of

---

### Post by Frak on 2009-01-11
> **adamogardner said:**
> Yes I dual boot from GRUB but this stuff just appeared somewhat recently.  and I'm not plugged into anything externally that I know of
You may be just seeing your XP partition.

---

### Post by adamogardner on 2009-01-12
> **Frak said:**
> You may be just seeing your XP partition.

Ok well let's say I was seeing Vista all of a sudden.  Why?  How do I move it?  Do I want to move it?  Is it really vista?  Which one?  what's the other?

---

### Post by adamogardner on 2009-05-21
> **Joeb454 said:**
> Slightly off-topic, but if one of those is a Windows dual boot, then boot into Windows and go into My Computer, rename the C drive (essentially, this gives it a label).

When you reboot into Ubuntu, it'll read whatever you named the C drive to, and list it as that under the Places menu.

This helps me distinguish between my drives :)

So if I changed C drive to "X"  it would read "X" under places.  This leads me to a new question.  Since it's listed in my places menu, can I do anything with it?  Like use it?

---

