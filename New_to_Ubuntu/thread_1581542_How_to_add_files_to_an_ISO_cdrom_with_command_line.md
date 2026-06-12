---
title: "How to add files to an ISO cdrom with command line?"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-25
Hello, 

I would like to add files to an ISO cdrom with command line?

Is there some possibilities for taht ; it is a bootable cdrom :(

---

### Post by mikewhatever on 2010-09-25
What is 'ISO cdrom'?

---

### Post by MrWES on 2010-09-25
> **honeybear said:**
> Hello, 

I would like to add files to an ISO cdrom with command line?

Is there some possibilities for taht ; it is a bootable cdrom :(
```
growisofs -dvd-compat -Z /dev/hdc=dvd.iso
```

Replace /dev/hdc with your device

Replace dvd.iso with your iso file name.

Bill

---

### Post by Bachstelze on 2010-09-25
> **honeybear said:**
> Hello, 

I would like to add files to an ISO cdrom with command line?

Is there some possibilities for taht ; it is a bootable cdrom :(

No, you can't add files to (or otherwise modify) an ISO9660 filesystem once it has been created. You have to recreate the filesystem with the missing file added.

---

### Post by honeybear on 2010-09-25
> **Bachstelze said:**
> No, you can't add files (or otherwise modify) to an ISO9660 filesystem once it has been created. You have to recreate the filesystem with the missing file added.

I heard that k3B could do the job. So if it is doing so, it might be possible since K3B is behind heavily command based ... surely

---

### Post by Bachstelze on 2010-09-25
> **honeybear said:**
> I heard that k3B could do the job.

And I'm telling you it can't. You can't modify an ISO9660 filesystem after it has been created. You can, however, create a new one that will be a duplicate of the old one, with the file added.

---

### Post by beew on 2010-09-25
> **Bachstelze said:**
> And I'm telling you it can't. You can't modify an ISO9660 filesystem after it has been created. You can, however, create a new one that will be a duplicate of the old one, with the file added.

What if you name the new one the same as the old one so the old one is overwritten? Would it in effect be modifying the old one?

---

### Post by Paul820 on 2010-09-25
> sudo apt-get install isomaster
You can add and extract files from the iso but you have to save it as another iso. In other words, the iso needs to be rebuilt.

---

### Post by honeybear on 2010-09-25
> **beew said:**
> What if you name the new one the same as the old one so the old one is overwritten? Would it in effect be modifying the old one?

I was considering winimage under windows, this one can add files to bootable cdrom or thre is winiso if I recall well.

I have to find back my qemu disk cow file so that I can try it ... find -iname is the key !

---

