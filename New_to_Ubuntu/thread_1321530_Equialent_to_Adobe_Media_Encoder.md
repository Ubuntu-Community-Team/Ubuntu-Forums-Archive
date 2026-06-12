---
title: "Equialent to Adobe Media Encoder"
date: 2009-11-10
forum: New to Ubuntu
---

### Post by smileyguy on 2009-11-10
I use Adobe Media Encoder through work to create flash files.

Is there anything equivalent in Ubuntu?

The Adobe Media Encoder is the only one so far I can get to convert cinematic wide screen and retain the correct screen aspect ration (1.85).

---

### Post by ikt on 2009-11-10
At worst is it possible to use Virtualbox or a vm of windows to use that program?

---

### Post by smileyguy on 2009-11-11
What is virtualbox & VM?

I just like to try and do whatever I do on Windows with free equivalents on Ubuntu.

---

### Post by Merk42 on 2009-11-11
What are you encoding to/from? You could try WinFF.

---

### Post by smileyguy on 2009-11-12
Encoding from AVI to flv.

---

### Post by 3rdalbum on 2009-11-12
FFMPEG supports the encoding of Flash Video (FLV). There are a few GUI frontends for FFMPEG, but it's actually pretty easy to use it on the command-line:

```
ffmpeg -i <input-file> -b 600kb output.flv
```

With those settings, the bitrate will be 600 kilobits per second, and the output file will be the same physical dimensions as the input file. You can specify a size manually if you want, like this:

```
-s 1920x1080
```

(or whatever it needs to be to be the desired aspect ratio).

You might need to install the "unstripped" versions of the libav libraries -  "libavcodec-unstripped-52", "libavdevice-unstripped-52", "libavfilter-unstripped-0", "libavformat-unstripped-52" etc. Just do a name search in Synaptic for "unstripped".

---

