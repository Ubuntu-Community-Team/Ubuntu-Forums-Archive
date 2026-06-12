---
title: "resize home partition"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by eddski on 2009-04-22
I know if I want to resize my /home, I have to do it with a live CD. I want to know how big a risk I run of damaging /home and what would be the best program to back it up and how would you copy ALL the files(including the hidden ones)? Also, can I resize any partition using a live CD? Sorry this is so long...

---

### Post by juancarlospaco on 2009-04-22
no risk, i use Back In Time for backup my /HOME on my /var/backup/backintime/
you can resize any partition using a live CD

---

### Post by ubunchu on 2009-04-22
You could also just create an archive of your /home and store it on an external device to restore it later. That's what I do currently, except with all of my partitions.

---

### Post by -kg- on 2009-04-22
Read the following from the Ubuntu Community Wiki:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

Especially read the last page on [Partition Editors and Backup software.]("https://help.ubuntu.com/community/HowtoPartition/EditorsAndBackup")

I just installed Back In Time and haven't had a chance to try it yet, nor have I had a chance to edit it into the Documentation page.  It sounds like a good piece of software (which of course is why I installed it).

Good luck! ):P

---

### Post by -kg- on 2009-04-22
> **juancarlospaco said:**
> no risk, i use Back In Time for backup my /HOME on my /var/backup/backintime/
you can resize any partition using a live CD

Just noticed this.  Is your /var partition on a partition separate from your /home partition?  If not, if you screw up your /home partition then your /var directory will go with it.

Best thing is to back it up to a separate partition, preferably on a separate hard drive, or on CD(s) or DVD(s).  That way you have a good backup in case the whole drive goes south.

---

### Post by eddski on 2009-04-23
thanks for the info, it is exactly what I was looking for.

---

