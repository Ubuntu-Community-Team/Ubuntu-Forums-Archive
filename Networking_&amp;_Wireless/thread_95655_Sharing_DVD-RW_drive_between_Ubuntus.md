---
title: "Sharing DVD-RW drive between Ubuntus"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by etitor on 2005-11-27
I have two workstations (let's call them PC "A" and PC "B" ). Both use Ubuntu Breezy. A NFS network lets me share files between them, both ways, through the router connection.

PC "A" has a printer. PC "B" hasn't got a printer. I can succesfully print from PC "B" using PC "A"'s printer.

Now PC "B" has a DVD-RW drive, and I would like to be able to burn CDs and DVDs from PC "A" (which has just a CD-ROM drive), using PC "B"'s drive.

I suppose it is possible. I have made /dev/cdrom in PC "B" "shared", the same way I "share" folders and files, but PC "A" cannot see the DVD-RW drive.

Can you point me to some help?

---

### Post by greenway on 2005-11-27
You shouldn't use the mounted DVD-RW, I don't think it's possible to remount an already mounted device. What you need to do is mount the device from dev/ (remote host) on the local host. This should work.

Oh and don't forget to export the device through /etc/exports.

---

### Post by mips on 2005-11-27
I would not advise you to burn CD's across a network as you might end up with lots of coasters. It is best to have the Data you want to burn and the drive on the same machine imho.

Nothing prevents you from trying though ;)

---

### Post by etitor on 2005-11-27
Thank you greenway, thank you mips. Both your contributions are of great value!

I think I will try to burn through my network just to test the theory. Of course a local copy of the data on the PC with the burner will be best.

---

### Post by greenway on 2005-11-28
I have also been thinking of trying the same thing, just for the fun of it! (the actual backups will go to the remote hosts first). So would you mind posting your experiences here? If I beat you to it, I will do the same thing! Thanks

---

