---
title: "CDROM won't open."
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Zanderist on 2010-09-03
I'm just after acquiring a new hard drive for my HP laptop.

 I'm trying to recover to windows through a recovery CD, however I cannot boot from my CD rom drive.


I ended up installing Ubuntu 10.04 'Lucid' (from a USB) to at least have an Operating system. I want to try and mount the recovery CD to a USB stick. If not that, fix the CDROM drive through Ubuntu.

  My problem is that I can't access the CD-ROM.

This is what I get in the terminal.
> $ sudo eject cdrom
eject: unable to find or open device for: `cdrom'


---

### Post by jtarin on 2010-09-03
Have you tried the command ```
eject

```Post results from the terminal command ```
eject -n
```

---

### Post by Zanderist on 2010-09-03
I did, and got the same message back.

> eject -n
eject: unable to find or open device for: `cdrom'


---

### Post by Ravenheart on 2010-09-03
Did you by any chance disturb the CD-ROM drive connections while fitting the hard drive? It sounds like a hardware type fault.

---

### Post by llamabr on 2010-09-03
It does sound a bit hardware-ee.  But your syntax may be wrong, too.  Try:

```
eject /cdrom
```

or 

```
sudo eject /cdrom
```

Though regular users should be able to access /cdrom.  Check fstab for that [separate problem].

---

### Post by Zanderist on 2010-09-03
> **Ravenheart said:**
> Did you by any chance disturb the CD-ROM drive connections while fitting the hard drive? It sounds like a hardware type fault.
It works in the start up (the bios screen?)

Not only that, the hard drive compartment is no where near the CDROM to cause any trouble.

Once Ubuntu is running it just stops.

I had the same problem when I still had vista running, but all I had to do was delete a certain 'install key' and it would reinstall it's self.

I also just tried the suggested terminal commands with these results:
> 
eject /cdrom
eject: tried to use `/cdrom' as device name but it is no block device
eject: unable to find or open device for: `/cdrom'
only difference was I was asked for a password when I used 'sudo'.

---

### Post by jtarin on 2010-09-03
run this command, as user, in the terminal to see if your a member of the cdrom group ```
groups
```

---

### Post by Zanderist on 2010-09-03
I am.

> adm dialout cdrom plugdev lpadmin admin sambashare

Anymore Ideas?

---

### Post by jtarin on 2010-09-04
Try this command ```
sudo lshw -C disk
```it should show your drives CD/DVD included.

---

### Post by Zanderist on 2010-09-05
Alright don't worry I  managed to get windows back on, and now I have a New Question.

---

