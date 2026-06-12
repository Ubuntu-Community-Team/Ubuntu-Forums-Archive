---
title: "ide harddisk read as  /dev/sda device?"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by wstay on 2009-01-31
I installed Ubuntu8.10 on an ide harddisk .
My System Monitor reports my ide harddisk as a /dev/sda device.
I don't understand why my ide harddisk is a /dev/sda device and not a /dev/hda device?
Can someone please explain.

---

### Post by x33a on 2009-01-31
this is because ubuntu marks the drives as sda or sdb and not hda etc. 

i think that previous versions of ubuntu (not sure which) used to call the drives hda or hdb.

---

### Post by wstay on 2009-02-01
> **x33a said:**
> this is because ubuntu marks the drives as sda or sdb and not hda etc. 

i think that previous versions of ubuntu (not sure which) used to call the drives hda or hdb.

But I thought sda for the first drive or sdb for the second drive are for SATA or SCSI harddisk.

---

### Post by bumanie on 2009-02-01
I can't remember with which version of ubuntu the naming protocol changed, (I think with 7.10), now hard drives, regardless of whether ide or sata or scsi are defined as sdx. I  presume this has been done for naming consistency, but really don't know. You are right, previously ide was defined as hdx.

---

### Post by lloyd_b on 2009-02-01
Linux *used* to put IDE drives as hda1, hda2, etc.  But some changes to the kernel (somewhere around the Gutsy version, IIRC) merged several different drivers (IDE, SATA, PATA) into a single package, with the result that what was formerly "hda..." became "sda...".

---

### Post by yeats on 2009-02-01
I would imagine this would have to do with the general move to laptops, which use SATA drives?  Just a guess.

---

### Post by x33a on 2009-02-01
i believe most modern desktops also use sata drives instead of ide.

---

