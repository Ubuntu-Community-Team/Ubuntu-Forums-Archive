---
title: "make my cd/dvd work"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by alf2 on 2010-10-26
Hi.
Looking at this file I think I see my floppy drive my two computer drives, one cd the other a dvd and the external dvd drive.
Why can I not use a disk in any of them to boot?
I can read from both dvds.
ls -l /media
total 16
drwxr-xr-x 21 root root 4096 2010-10-16 21:19 80e812ef-df28-4129-8c48-7eba067d309a
lrwxrwxrwx  1 root root    6 2010-01-12 20:25 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2010-01-12 20:25 cdrom0
drwxr-xr-x  2 root root 4096 2010-01-12 20:25 cdrom1
lrwxrwxrwx  1 root root    7 2010-01-12 20:25 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2010-01-12 20:25 floppy0

---

### Post by janpol on 2010-10-26
Have you set your BIOS to boot from the CD/DVD drive first?

---

### Post by alf2 on 2010-10-26
My bios only sees a floppy and a hard drive

---

### Post by janpol on 2010-10-26
Are you shure you can't select your CD-ROM drive in the Boot Section?

Take a look at this: [http://www.hiren.info/pages/bios-boot-cdrom]("http://www.hiren.info/pages/bios-boot-cdrom")

---

