---
title: "Ubuntu workstation computer name ?"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by wpshooter on 2006-08-29
I read in a post here the other day, that if I wanted to use SAMBA to possibly do Ubuntu workstation printer sharing, that all of my Ubuntu workstations should be given the **same name** on my home network.  Is that true ?  

If I named all 4 computers on my home network "WPSHOOTER-UBUNTU" would this not confuse Ubuntu desktop operating system ?  Because as I remember, the terminal prompt for my 4 computers now are wpshooter@Ubuntu-1, wpshooter@Ubuntu-2, wpshooter@Ubuntu-3 and wpshooter@Ubuntu-4.

Thanks.

---

### Post by DarthMandeep on 2006-08-29
They should not be given the same hostname, but the same domain.

---

### Post by mssever on 2006-08-29
The computers should *not* have the same name. What *should* be the same is the workgroup set in /etc/samba/smb.conf. You can also set this in System > Administration > Shared Folders.

---

