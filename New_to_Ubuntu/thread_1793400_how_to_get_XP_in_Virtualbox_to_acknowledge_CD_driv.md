---
title: "how to get XP in Virtualbox to acknowledge CD drive"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by s1baker on 2011-06-29
hi,
I can't get Windows XP running as a guest OS under Virtualbox to read the CD player. I have Ubuntu 10.10 32 bit.

When I first go into virtualbox and run XP, I can eject the CD tray in XP, so I know XP is aware that the CD player is there, but when I place a music disk in the CD tray and close it, XP responds back that the disk is un-readable. When I go back into Ubuntu, I see that Ubuntu has mounted the CD, I guess by the process of the CD tray being opened and then closed with a disk Ubuntu took control of it, but I don't know.
 Maybe the CD would need to be unmounted in Ubuntu before XP in VB can see it? I don't know how to un-mount the CD though.

Anybody know anything about this?

Thanks

---

### Post by haqking on 2011-06-29
> **s1baker said:**
> hi,
I can't get Windows XP running as a guest OS under Virtualbox to read the CD player. I have Ubuntu 10.10 32 bit.

When I first go into virtualbox and run XP, I can eject the CD tray in XP, so I know XP is aware that the CD player is there, but when I place a music disk in the CD tray and close it, XP responds back that the disk is un-readable. When I go back into Ubuntu, I see that Ubuntu has mounted the CD, I guess by the process of the CD tray being opened and then closed with a disk Ubuntu took control of it, but I don't know.
 Maybe the CD would need to be unmounted in Ubuntu before XP in VB can see it? I don't know how to un-mount the CD though.

Anybody know anything about this?

Thanks

from the top menu of the VM choose devices and click on your cd, this should unmount it from Linux in some sintances and then you will have it as a drive in your VM ?

this needs to be ticked in the VM settings though as having access to your host drive.

---

### Post by pqwoerituytrueiwoq on 2011-06-29
visual reference
i don't think you can burn a cd/dvd though

---

### Post by s1baker on 2011-06-29
In XP, under devices, the "host drive ATAPI iHap322 9 (sr0)"
is checked. I tried to uncheck it and then I checked it back, but still could not get it to work. Unbuntu shows it mounted.

---

### Post by howefield on 2011-06-29
Have you enabled the "passthrough" option for the drive ?

---

### Post by s1baker on 2011-06-29
I tried to select passthrough, but that didn't work either.
I think I may need to unmount the CD in Ubuntu because when the CD door is opened in XP, the CD mounts in Ubuntu, but I don't know how to unmount it.

---

### Post by pqwoerituytrueiwoq on 2011-06-29
cd is set to sr0 in setting and passthrough is checked 
i am looking at the cd in ubuntu and xp  at the same time
edit:
you could eject the cd and close the disk drive
```
eject /dev/sr0
eject /dev/sr0 -t
```

---

### Post by howefield on 2011-06-29
> **s1baker said:**
> I think I may need to unmount the CD in Ubuntu because when the CD door is opened in XP, the CD mounts in Ubuntu, but I don't know how to unmount it.

Try the terminal command..

```
sudo umount /media/cdrom0/
```

---

### Post by s1baker on 2011-06-29
I can't find where it is mounted.
I have a /media/floppy & a /media/floppy0
Also, I have a /mnt/floopy0 & a /cdrom/ that is empty
The CD is working though, I just clicked on the Ubuntu desktop icon for it and got a listing of the music files there

---

### Post by s1baker on 2011-06-29
here is a screenshot of my settings for the storage in XP.
If I try to check "passthrough", when XP boots up, there is no icons on the screen or even a title bar. I have to het the "x" in the top right corner of the screen to get out of XP.

---

