---
title: "joining video files"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-10-15
I downloaded 5 video files (.avi) from the internet and wanted to join them using cat. 

I gave the following command

cat F1 F2 F3 F4 F5 > F

Even though the size of the file F is the sum of the sizes of all the files, but using mplayer I find that only F1 and F2 have been merged. Where does the other data disappear?

Thanks

---

### Post by TeoBigusGeekus on 2010-10-15
[http://ffmpeg.org/faq.html#TOC27]("http://ffmpeg.org/faq.html#TOC27")

---

### Post by LittleGyko on 2010-10-15
A single file was broken into 5 parts and posted on the net. 

The above method does not seem to work as when i try to convert the second file, i get the error " unknown format".

---

### Post by dr_kabuto on 2010-10-15
You can use also Avidemux, which can join splitted video files. Open the first file, then add the other ones with the Add... menu option (one file at time).

---

### Post by matt_symes on 2010-10-15
Hi,

That wont necessary work. It will concatenate the files, but the files could contain markers depending on how they are split.

Use video editing software

[http://techcityinc.com/2009/02/04/top-10-free-video-editors-for-ubuntu-linux/](http://techcityinc.com/2009/02/04/top-10-free-video-editors-for-ubuntu-linux/)

Kind regards

---

