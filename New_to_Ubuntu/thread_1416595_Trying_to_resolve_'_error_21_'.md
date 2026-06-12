---
title: "Trying to resolve ' error 21 '"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by L Campbell on 2010-02-26
I have an 'error 21'on my hard drive and have not been able to find any info about how to correct it in this forum.

Do you have a suggestion?

TIA

---

### Post by donkyhotay on 2010-02-26
When/where are you getting that message?

---

### Post by Kakers on 2010-02-26
Yup, search google :D

> 
**Reinstalling or fixing Grub after error 21: **
 
[LIST=1]
[*]Boot into the original Linux system with the hard drive still installed (or you can boot from a Live Ubuntu CD).
[*]Open up a terminal and type **sudo su**
[*]Type **fdisk -l** and locate your Linux boot partition from the list **Example**: **sda1**
[*]Type **grub-install /dev/sdx** to reinstall or repair Grub!
[*]Reboot and test!
[COLOR=#800000]**Notes:**[/COLOR] **x** represents the drive letter **a, b, c, d** etc. Replace with your actual drive letter.
[/LIST]


---

### Post by mikeyphi on 2010-02-26
Is this error during boot...possible with something about Grub just before?

If so it indicates that grub can't find the HD it's looking for, reasons could be:
you've reinstalled/updated windows
you've changed the boot order in BIOS

you might need to use a Live-CD and run 'update-grub'

---

### Post by L Campbell on 2010-02-26
> **Kakers said:**
> Yup, search google :D

Thanks, I'm operating with the Live CD here:-


ubuntu@ubuntu:~$ sudo su

root@ubuntu:/home/ubuntu# fdisk -l



Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7c2c7c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris
root@ubuntu:/home/ubuntu# grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
root@ubuntu:/home/ubuntu# 

It appears that I did something wrong here????

---

### Post by mikeyphi on 2010-02-26
Might need to 'mount' the drive before grub-install?

---

### Post by L Campbell on 2010-02-26
> **mikeyphi said:**
> Might need to 'mount' the drive before grub-install?

OK, I do have the HD mounted.  It is because I couldn't get it to work properly that I then booted up with the Live CD.

---

