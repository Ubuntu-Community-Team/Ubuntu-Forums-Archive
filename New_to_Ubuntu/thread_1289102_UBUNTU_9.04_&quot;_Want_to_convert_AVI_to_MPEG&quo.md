---
title: "UBUNTU 9.04 &quot; Want to convert AVI to MPEG&quot;"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by appoloin on 2009-10-12
Could someone advise me what i can use to convert AIV toMPEG in UBUNTU? i use to use winavi but that dont work in linux.

---

### Post by Cresho on 2009-10-12
winff, medibuntu needs to be installed first.

this is my preset
-vcodec mpeg1video -b 20000K -acodec mp2 -ab 320k -ar 48000 -ac 2

---

### Post by appoloin on 2009-10-12
HEy thank..

sorry for the very dumb question here..

this is my preset
-vcodec mpeg1video -b 20000K -acodec mp2 -ab 320k -ar 48000 -a

i found Preset.. not sure where all the above goes?

---

### Post by Paqman on 2009-10-12
Avidemux is available in the repos, or you can download a .deb of Handbrake from their site. I prefer Handbrake because it's multi-threaded.

---

### Post by lavinog on 2009-10-12
+1 avidemux for a gui way.
I prefer mencoder though.

Why do you need the avi converted to mpeg?

---

### Post by appoloin on 2009-10-12
SOme of my AVI movies dont play on my DVD player so i convert it to MPEG

---

### Post by mikechant on 2009-10-12
DeVeDe is fine for this as well if you want a straightforward gui. It's primary purpose is to produce a complete DVD disc structure, including video format conversion, but you can tell it just to produce mpeg files instead. It can convert a variety of files including flv (flash) and avi.
I believe it uses mencoder behing the scenes to do the format conversions.

---

