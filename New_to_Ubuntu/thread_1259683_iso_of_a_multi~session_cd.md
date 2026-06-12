---
title: "iso of a multi~session cd"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by macanudokiosko on 2009-09-06
dd if=/dev/cdrom of=/home/test1.iso  this command has rendered an iso-image, which was of the original session. It didn't include all other sessions.  (I use CD-Roller through Wine, and I need to access previous sessions of cd-isos.)  macanudokiosko

---

### Post by Liolikas on 2009-09-06
mkisofs

---

### Post by macanudokiosko on 2009-09-06
mkisofs -r -J -o '/home/marcus/cdimage.iso' /media/cdrom0  This example seems resolving it, but I can't reach the previous seasons through Cd-Roller+Wine.  Is there any similar program, like CD-Roller?  tx macanudokiosko  > **Liolikas said:**
> mkisofs

---

