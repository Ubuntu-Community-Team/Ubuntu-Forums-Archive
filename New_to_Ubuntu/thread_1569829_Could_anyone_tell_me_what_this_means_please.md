---
title: "Could anyone tell me what this means please?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by cheekymonky2010 on 2010-09-07
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4040B A106 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW) [DVD-ROM, DVD-R Sequential, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite] [%7]

System
-----------------------
K3b Version: 1.91.0
KDE Version: 4.4.2 (KDE 4.4.2)
QT Version:  4.6.2
Kernel:      2.6.32-24-generic

Used versions
-----------------------
mkisofs: 1.1.10

this is the message I got from k3b when it failed to burn a dvd!

---

### Post by silverglade00 on 2010-09-07
That just looks like a description of the parts of your system relevant to burning a dvd. The first part describes your CD/DVD burner. The second part describes the software versions that k3b is using. The third part shows which command line program and version are "under the hood" that k3b uses to work its magic. You can probably look in /var/log/messages or System-Administration-Log File Viewer to get more info on why it didn't burn correctly.

---

### Post by viralmeme on 2010-09-07
> **cheekymonky2010 said:**
> this is the message I got from k3b when it failed to burn a dvd!

Restricted Overwrite possible means you are trying to re-write to a rewritable DVD that's incompatible or full ..

---

### Post by cheekymonky2010 on 2010-09-07
Ok thanks!  I just tried Brassero and it worked with the same dvd! so I think I will stick with that!

---

