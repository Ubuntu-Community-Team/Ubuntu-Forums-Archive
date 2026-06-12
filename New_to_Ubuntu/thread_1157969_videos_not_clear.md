---
title: "videos not clear"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by bobin on 2009-05-13
hey
no videos that i play are clear as in some colours are totally missing. Eg- blue comes in place of red and brown . I have tried totem and VLC
Help...

---

### Post by stephanvaningen on 2009-05-13
Have you installed the medibuntu-modules?
Do this:
```
sudo su
*(enter password)*

wget http://www.medibuntu.org/sources.list.d/jaunty.list --output-document=/etc/apt/sources.list.d/medibuntu.list

apt-get update
apt-get install medibuntu-keyring
apt-get update

apt-get install libdvdcss2 w32codecs gstreamer0.10-plugins-ugly-multiverse ffmpeg
*(replace 32 by 64 if applicable)*
exit

```
I use these packages to have good video-processing with codecs

---

