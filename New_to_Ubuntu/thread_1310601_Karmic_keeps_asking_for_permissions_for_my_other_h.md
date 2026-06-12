---
title: "Karmic keeps asking for permissions for my other hard drive"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2009-11-01
So I have a 1.5 tb drive formatted to ext3 that I use to store all of my media files.

On Ubuntu 9.04 it would mount the drive automatically with the proper permissions as soon as I clicked on it.

Now in 9.10 it asks me to enter my password every time I mount the thing by clicking on it.  Any way to get this to just store the password or something?

---

### Post by sahabcse on 2009-11-01
Try to set the auto-mount using /etc/fstab

---

### Post by CryptiniteDemon on 2009-11-01
Meh, I thought it had progressed past the point of ever having to use fstab again manually.  Funny how I always feel like I'm using 6.06 every time Ubuntu releases a new version.

---

### Post by JBAlaska on 2009-11-02
9.10 Nautilus only asks for my PW on Non-Linux partitions/drives (NTFS), and since I use Krusader in root mode (Cause I don't need to be protected from myself) for my main file manager, I only have to enter the PW once.

Guess you could use sudoers to fix it...oops, did I say that out loud lol.

---

### Post by arito on 2009-11-04
Same problem here. Automount used to work in 9.04, but in my (installed, not upgraded) 9.10 I have to give the password to access other partitions every time I boot the system. This is frustrating, because if I forget to mount those partitions, Transmission won't find the partially downloaded files, and gives an error message. After mounting the partitions, I have to run "check downloaded data" for all partially downloaded files (very frustrating, when you have 30 GB of downloads in progression). My back-up software also doesn't work, when the partitions are not mounted.

This is clearly a regression in Ubuntu 9.10.

---

### Post by CryptiniteDemon on 2009-11-15
Well I finally got around to changing my fstab file.  There's a bug in gnome that when I put the drive in fstab by its uuid then it shows up twice in the "system" menu.  So irritating.  So I had to change it to the /dev address instead.

---

### Post by howefield on 2009-11-15
> **CryptiniteDemon said:**
> Meh, I thought it had progressed past the point of ever having to use fstab again manually.

Meh, use the GUI in that case.

---

