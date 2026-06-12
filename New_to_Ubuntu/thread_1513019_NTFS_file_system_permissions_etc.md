---
title: "NTFS file system permissions etc"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by cetacean on 2010-06-18
Hey, what is the deal with "permissions"?

I am dual-booting Windows 7 and Lucid, with most of my important stuff in the NTFS partition.

Should I be concerned about working with files in the NTFS partition while in Ubuntu programs? Is there anything more than a remote chance that I am going to corrupt them just by opening them, working with them, and re-saving them?

It would be devastating if I lost important stuff just because I tried to access it from both directions.

thank you

---

### Post by sandyd on 2010-06-18
> **cetacean said:**
> Hey, what is the deal with "permissions"?

I am dual-booting Windows 7 and Lucid, with most of my important stuff in the NTFS partition.

Should I be concerned about working with files in the NTFS partition while in Ubuntu programs? Is there anything more than a remote chance that I am going to corrupt them just by opening them, working with them, and re-saving them?

It would be devastating if I lost important stuff just because I tried to access it from both directions.

thank you
there shouldn't be any problems, ntfs-3g has been around for a while now, and has probably most of its major bugs fixed by now.

---

### Post by nhasian on 2010-06-18
you shouldn't have any problem reading and writing to your NTFS partitions.  I think by default the NTFS partition(s) are not mounted but you can mount them just by clicking on them in the places menu.  if you use it frequently you probably want to add the NTFS partition to your /etc/fstab so it will be auto-mounted on startup.

---

