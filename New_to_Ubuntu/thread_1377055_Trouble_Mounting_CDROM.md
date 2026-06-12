---
title: "Trouble Mounting CDROM"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by StylusJunky on 2010-01-09
Having trouble mounting cdrom drive.  I have used #mount with what I thought was the name that ubuntu gave it.  Nothing at all happened except it gave me a new command prompt.  I am relatively new to linux. I did use it a little bit in college, but I am still very new to it.  

sda:
Clocksource tsc unstable (delta = -88398743 ns)
sda1 sda2 < sda5 >
sd 0:0:0:0: [sda] Attached SCSI disk
ata2.00: configured for UDMA/33
scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K17A 1.50 PQ: 0 ANSI: 5
sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Uniform CD-ROM driver Revision: 3.20
sr 1:0:0:0: Attached scsi CD-ROM sr0
sr 1:0:0:0: Attached scsi generic sg1 type 5

Any suggestions as to the name or maybe an easier way?

Thanks

---

### Post by aaronp on 2010-01-09
Hi,
using mount (with no #) will only show you what is currently mounted.
Using ```
sudo mount -a
``` will mount everything that is specified in your /etc/fstab file. 
Try that first and see if it works. Has this cdrom drive been mounted before?
If so it is probably in fstab. You can do ```
gedit /etc/fstab
``` from the terminal to inspect the file and see if the cd drive is there.

If you have no luck, paste the contents of your fstab here.

---

### Post by CharlesA on 2010-01-09
The cdrom should be mounted to media/cdrom.

As aaronp said, try just running "mount" (no quotes) to see what is mounted.

---

### Post by brij on 2010-01-11
you need to enter a line like the following if its not there


/dev/scd0      /mnt/cdrom      udf,iso9660   user,noauto,exec,utf8   0 0

---

