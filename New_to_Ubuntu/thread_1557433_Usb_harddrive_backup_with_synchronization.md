---
title: "Usb harddrive backup with synchronization"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by purplearcanist on 2010-08-20
I have a ubuntu installation (10.04) that I want to backup on a USB hard drive.  Additionally, I want to be able to boot this installation from the hard drive, having a clone of my system bootable on a different computer, and the files available when I plug the drive into a windows or macintosh.  Finally, I want to be able to synchronize files between the usb hard drive and my computer, preferably with a single command.

I have searched through several ubuntu guides, and while some mention cloning an installation, or backing up your hard drive, they don't specify how to do all of this.  I would like all of this, but even a solution that can accomplish most of this would be helpful.

---

### Post by purplearcanist on 2010-08-21
tap can anyone help

---

### Post by earthpigg on 2010-08-21
hi,

you've checked out remastersys, right? it gives you an .iso that you can put on a thumb drive using either unetbootin or ubuntu's startup disk creator in system -> admin.

---

### Post by purplearcanist on 2010-08-21
> **earthpigg said:**
> hi,

you've checked out remastersys, right? it gives you an .iso that you can put on a thumb drive using either unetbootin or ubuntu's startup disk creator in system -> admin.

I am going to check it out.  I will make another post if I have any more questions.

Thank you for pointing this out, it looks like a good solution.

---

### Post by mapes12 on 2010-08-22
I'm not sure that one app alone can accomplish your requirements. As earthpigg has suggested Remastersys is a good choice for cloning. You could also look at:

Clonezilla
Partimage
FSarchiver

For syncing your stuff I would use Grsync.

As for resource, cloning means you will be copying everything regardless of whether data from the last clone process has changed or not. Syncing only updates stuff that's modified or new, and therefore much quicker.

I use a combination of:-

Remastersys - for my UBU OS installation
Grsysnc - for my /home data

I have / and /home on separate partitions which makes live easier.

---

