---
title: "change .oog files to mp3"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by bob brazie on 2011-01-02
Ubuntu 10.10

I need to change some .oog music files to MP3 so my wife can listen to them on her I-shuffle.

I tried a goggle search but came up empty.

Any help will make a Ubuntu fan of her. <g>

Thanks in advance. Bob.

---

### Post by TeoBigusGeekus on 2011-01-02
```
ffmpeg -i nameoffile.ogg -acodec libmp3lame -ab 320k nameoffile.mp3
```

---

### Post by howefield on 2011-01-02
Soundconverter (in Software Centre) or if you prefer the command line, there is ffmpeg.

---

### Post by Verbeck on 2011-01-02
*~edited out~*

---

### Post by Mindswap1 on 2011-01-02
There is a lot of software that converts .oog files, but I have to say ffmpeg is the best. And there is a simple add on that will give you a gui. 

Simply open up software center, and search ffmpeg. There should be a bunch of results, but what you want is the first one, which says mutimedia player, server and encoder. Download that. 

Also you want to install one more thing. Search ffmpeg once more, and you should see something named Winff there. Install that. Once thats done simply go to Applictions>Sound&Video> and then WinFF.

Also please note ffmpeg is not only command line based if you install Winff, which addeds a program like environment. enjoy

---

### Post by bob brazie on 2011-01-03
Thanks that did the trick!

---

