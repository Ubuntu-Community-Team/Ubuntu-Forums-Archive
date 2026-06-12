---
title: "sda / hda - What's the Point?"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by Penguin Guy on 2009-07-27
I understand that the Linux kernel assigns the prefix [COLOR="Green"]hd[/COLOR] to IDE drives and [COLOR="Green"]sd[/COLOR] to everything else.

1: Why stop at two prefixes? Why not have, say; 
[LIST]
[*][COLOR="Green"]fd[/COLOR] (flash drive)
[*][COLOR="Green"]id[/COLOR] (SCSI)
[*][COLOR="Green"]sd[/COLOR] (SATA)
[*][COLOR="Green"]hd[/COLOR] (IDE)
[*][COLOR="Green"]od[/COLOR] (unknown)
[/LIST]

2: Why have it at all? Most users won't be bothered too much about what kind of device something is, and if they could use some command like [COLOR="Green"]lspci[/COLOR] or whatever.

3: My IDE drive is detected by the kernel as [COLOR="Green"]sda[/COLOR] - is this a kernel error or is there something wrong with my (home-made) computer.

---

### Post by Barrucadu on 2009-07-27
I believe everything was changed to sd* in the kernel a while back, but Ubuntu hasn't got that yet. Or something. I could be completely wrong.

---

### Post by halitech on 2009-07-27
actually they changed things in the kernel a version or 2 back and now all drives are seen as sdX, doesn't matter if it is IDE, Sata, thumb drive, whatever.

Reason they have it (to my understanding) is they need to have some way to identify hard drive.

---

### Post by sisco311 on 2009-07-27
> **Penguin Guy said:**
> 
3: My IDE drive is detected by the kernel as [COLOR="Green"]sda[/COLOR] - is this a kernel error or is there something wrong with my (home-made) computer.

The IDE subsystem in the linux kernel has been functionally replaced by the PATA subsystem which uses the sdX naming convention.

---

### Post by Penguin Guy on 2009-07-27
So, as I understand it, each hard drive module has it's own prefix convention and, by complete coincidence, all the prefixes happen to be the same at the moment?

---

### Post by aesis05401 on 2009-07-27
*snip*

---

### Post by aesis05401 on 2009-07-27
Explanation:

[http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce]("http://kernelnewbies.org/Linux_2_6_19#head-cdcbaa9c1b476decdc064e0a75d23d1328b1ddce")

---

### Post by 3rdalbum on 2009-07-27
> **Penguin Guy said:**
> I1: Why stop at two prefixes? Why not have, say; 
[LIST]
[*][COLOR="Green"]fd[/COLOR] (flash drive)
[/LIST]

I think "fd" is "floppy disk".

---

### Post by nandemonai on 2009-07-27
> **3rdalbum said:**
> I think "fd" is "floppy disk".

Sure is ;)

---

### Post by earthpigg on 2009-07-27
> **3rdalbum said:**
> I think "fd" is "floppy disk".

what is a floppy disk?

---

### Post by halitech on 2009-07-27
something that is pretty much extinct in newer computers

[http://en.wikipedia.org/wiki/Floppy_disk](http://en.wikipedia.org/wiki/Floppy_disk)

> A floppy disk is a data storage medium that is composed of a disk of thin, flexible ("floppy") magnetic storage medium encased in a square or rectangular plastic shell. Floppy disks are read and written by a floppy disk drive or FDD, the initials of which should not be confused with "fixed disk drive," which is another term for a (nonremovable type of) hard disk drive. Invented by IBM, floppy disks in 8-inch (200 mm), 5¼-inch (133.35 mm), and 3½-inch (90 mm) formats enjoyed many years as a popular and ubiquitous form of data storage and exchange, from the mid-1970s to the late 1990s. While floppy disk drives still have some limited uses, especially with legacy industrial computer equipment,[2] they have now been largely superseded by USB flash drives, External Hard Drives, CDs, DVDs, and memory cards (such as Secure Digital).

---

### Post by muteXe on 2009-07-27
> **earthpigg said:**
> what is a floppy disk?

It's something you get after too much beer.


Ohhhh sorry thought you typed something else...

---

