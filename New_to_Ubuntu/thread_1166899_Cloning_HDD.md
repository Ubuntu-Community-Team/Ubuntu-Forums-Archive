---
title: "Cloning HDD"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by timbim on 2009-05-22
If I were to boot off, say, system rescue cd, or indeed any other live cd, and to issue the command in the terminal ```
dd if=/dev/sdb of=/dev/sdc
```that would copy the entirety of sdb onto sdc, would it not (provided that sdb is smaller than sdc)

Is this the best way to copy all the data, including partition tables etc onto a new HDD?

---

### Post by NHArticleTen on 2009-05-22
[http://www.clonezilla.org/](http://www.clonezilla.org/)

[http://en.wikipedia.org/wiki/Clonezilla](http://en.wikipedia.org/wiki/Clonezilla)

---

### Post by lkraemer on 2009-05-22
Ditto!  Clonezilla!

lkraemer

---

### Post by logos34 on 2009-05-22
if clonezilla, you'd want to select ['disk-to-disk']("http://www.clonezilla.org/clonezilla-live/doc/") copy option
EDIT: Normally clonezilla uses partimage, partclone or ntfsclone to copy only the USED sectors.  And after checking it appears that it also copies only used space for whole disk-to-disk mode. Nice

Here's the exact dd command you would want to use if that is the tool you prefer (it *is* simpler, albeit slow):
> 
dd if=/dev/sdb of=/dev/sdc bs=4096 conv=notrunc,noerror

Notrunc means 'do not truncate the output file'. Noerror means to keep going if there is an error. Normally dd stops at any error.

---

### Post by bpalone on 2009-05-22
Another option is to use GParted either the live CD of it or use it off of your Ubuntu Live CD.  I have used the GParted Live CD to migrate to a larger HD and it went smoothly.  Just use the copy and paste.

---

### Post by timbim on 2009-05-23
So if I just copy the partitions, All the partition table data etc will be conserved, correct?  That won't cause any problems?

---

### Post by logos34 on 2009-05-23
> **timbim said:**
> So if I just copy the partitions, All the partition table data etc will be conserved, correct?  That won't cause any problems?

no, the partition table (+ bootloader) is on the MBR at the front of the disk.  If you just copy individual partitions one at a time (with Gparted, say), you have to do the mbr separately.  But when you do the whole disk (to-disk) at once it copies everything.

---

### Post by timbim on 2009-05-23
> **logos34 said:**
> ```
dd if=/dev/sdb of=/dev/sdc bs=4096 conv=notrunc,noerror 
```What does the bs=4096 do?

---

### Post by HermanAB on 2009-05-23
Howdy,

You could also copy over a network:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

---

### Post by timbim on 2009-05-23
Don't have a reason to do that, this is to let me swap my HDD for a bigger one, using a new caddy.

---

### Post by timbim on 2009-05-23
I've read up on the dd command, is there any particular reason to make bs=4092?  Does it make a difference what it is set to?

---

### Post by logos34 on 2009-05-23
I think the default is 2048...Using a bigger block size is faster I believe

---

