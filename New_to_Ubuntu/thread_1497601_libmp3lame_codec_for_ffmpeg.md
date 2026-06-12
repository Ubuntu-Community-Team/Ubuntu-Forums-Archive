---
title: "libmp3lame codec for ffmpeg"
date: 2010-05-30
forum: New to Ubuntu
---

### Post by vagelis4209 on 2010-05-30
hi guys ,

im using ubuntu 10.04 and i want ffmpeg to be able to use libmp3lame codec..

Any ideas how i can do that??

ty...:):)

---

### Post by NightwishFan on 2010-05-30
If it is not installed, try the unstripped libav (and etc) or the medibuntu repository.

[Install Unstrippted Libav]("apt://libavcodec-extra-52")
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by bildr on 2010-05-30
enable all repos and apt-get install ubuntu-restriced-extras

---

### Post by vagelis4209 on 2010-05-31
> **bildr said:**
> enable all repos

How am i supposed to do that??

thanx!!:)

---

### Post by FakeOutdoorsman on 2010-05-31
You need to install one package to enable *libmp3lame* in FFmpeg and is explained here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

