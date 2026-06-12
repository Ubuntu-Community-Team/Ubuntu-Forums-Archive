---
title: "OS crashed, how do i backup files through command line?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by Velenjak on 2011-02-28
ubuntu 9.10 to 10.04

my computer crashed during an upgrade.

most of my information is already backed up but i want to transfer a couple more files.

can someone direct me to a good write-up or show me the different commands i need to know to move files to a usb?

---

### Post by Hedgehog1 on 2011-02-28
> **Velenjak said:**
> ubuntu 9.10 to 10.04

my computer crashed during an upgrade.

most of my information is already backed up but i want to transfer a couple more files.

can someone direct me to a good write-up or show me the different commands i need to know to move files to a usb?

Velenjak,

If you boot from the 10.04 CD you have and do the 'try' option, you should be able to see your Hard Disk and any USB stick you insert in the 'places' menu.

You can then copy the data in the GUI.

Start there.  

If you find the Hard Disk is not readable, there are other steps that need to be done.

:KS

---

### Post by Velenjak on 2011-02-28
> **Hedgehog1 said:**
> Velenjak,

If you boot from the 10.04 CD you have and do the 'try' option, you should be able to see your Hard Disk and any USB stick you insert in the 'places' menu.

You can then copy the data in the GUI.

Start there.  

If you find the Hard Disk is not readable, there are other steps that need to be done.

:KS

no files are listed under the places menu... what should i do?

i want to backup a some tomboy notes and a couple other file

---

### Post by Hedgehog1 on 2011-02-28
> **Velenjak said:**
> no files are listed under the places menu... what should i do?

i want to backup a some tomboy notes and a couple other file

get to the terminal, and try to mount the partitions manually:

```
sudo mount -a
```

And see if that shows you your partitions in 'places'

Remember - you need to get to the hard drive - NOT the local folders on the live CD.

Otherwise I will need to turn this over to other forum members...

---

### Post by HermanAB on 2011-03-01
howdy,

Always remember that rsync is your friend - it is a better kind of copy.  it is especially helpful when you already copied some files and now want to refresh the backup.  

Rsync will only copy the things that changed and thereby save you oodles of time.  The rsync man page is very good - read it.

---

