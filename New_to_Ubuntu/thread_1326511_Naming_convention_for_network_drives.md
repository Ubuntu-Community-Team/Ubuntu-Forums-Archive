---
title: "Naming convention for network drives"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by grumpyoldgit on 2009-11-14
I am having a bit of difficulty getting my head round the naming conventions used for naming network drives.
I wish to back-up data from my usb drive to a share on my Freenas nas.
I am happy that the share on the usb is called /media/usb drive/downloads/ as grsync can see the share and count the files.
In the file manager I have seen the freenas share named as smb://freenas.local/data2/ but if I use that name the hostname cannot be resolved.

---

### Post by Paqman on 2009-11-15
I normally mount my network shares to a permanent mount point, but you'll probably find that the file manager will mount them to a folder in /media as well.

---

