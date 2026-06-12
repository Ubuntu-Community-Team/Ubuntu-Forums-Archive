---
title: "Looking a sort of PHOTOREC for  scratched CDROM (damaged) (I made an ISO)"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-22
Hi, 
a blank cdrom which is not actually. How to recover this cdrom? it seems there is not app for that :( 

Cheers

---

### Post by mikewhatever on 2010-11-23
I don't know if you can run Photorec on an iso file; should be worth checking. Recoverjpeg is another tool from the repositories for recovering pictures.

---

### Post by SecretCode on 2010-11-23
You may need to run **ddrescue** to recover raw data from the CD to an image file, and then run something like photorec on the image file. Something like

```
sudo ddrescue -nv /dev/cdrom ~/mycdrom.img ~/mycdrom.log
sudo ddrescue -dvr 2 /dev/cdrom ~/mycdrom.img ~/mycdrom.log
```

See [GNU ddrescue Manual]("http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html") before you start

---

