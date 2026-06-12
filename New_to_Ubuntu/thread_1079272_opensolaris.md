---
title: "opensolaris"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by sameer.india on 2009-02-24
i had ubuntu installed and the installed opensolaris (2nd last partition just above swap).
i had backed up my menu.lst from ubuntu.
then i copied the entry list to /rpool/boot/grub/menu.lst.
when i select that entry during boot it says file not found

---

### Post by swoll1980 on 2009-02-25
> **sameer.india said:**
> i had ubuntu installed and the installed opensolaris (2nd last partition just above swap).
i had backed up my menu.lst from ubuntu.
then i copied the entry list to /rpool/boot/grub/menu.lst.
when i select that entry during boot it says file not found

burn off a super grub disk it will find your Ubnutu install and write the grub accordingly

---

### Post by sameer.india on 2009-02-26
I don't know about super grub disk but the grub from the intrepid live cd and the open solaris grub refuse to detect an operating system. I also made the ubuntu root partition active. But that just gives
[I]Bad PBR Sig
No Operating system found[/I]

---

### Post by Sirron on 2009-02-26
When you say OpenSolaris, do you mean Nexenta by any chance?

---

