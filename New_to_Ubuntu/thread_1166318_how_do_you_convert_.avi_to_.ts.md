---
title: "how do you convert .avi to .ts?"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by iwannalearn on 2009-05-21
Hi all, been away one windoz for a while but came back agian to ubuntu, to stay i hope.

so when i was on doz i used to download a backup film then use a free software "Quick Media Converter" to convert it to dreambox format which is .ts

then i would ftp over to my dreambox hdd and watch on my tv.

can someone point me in the right direction to do this using ubuntu mainly the conversion part.

thanks a lot

ps i did try the search

---

### Post by rob2uk on 2009-05-21
Tried avidemux?

---

### Post by iwannalearn on 2009-05-21
Thanks, i have just installed avdmux

how do you use it:oops:

i did open and selected the avi file i want to convert, but have now idea what next!

---

### Post by Jose Catre-Vandis on 2009-05-21
Could try ffmpeg
```
ffmpeg -i input.avi -vcodec copy -acodec copy -f mpegts output.ts
```

or here is a link to a blog that does it with mencoder
```
http://kalfaoglu.com/wp/?p=5
```

---

### Post by iwannalearn on 2009-05-22
I tried 

ffmpeg -i input.avi -vcodec copy -acodec copy -f mpegts output.ts

But got this and did not work, please help

thanks

xxxxxxxx@desktop:~/Desktop/BMW$ ffmpeg -i BMW.wmv -vcodec copy -acodec copy -f mpegts BMW.ts
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, asf, from 'BMW.wmv':
  Duration: 00:04:49.74, start: 3.000000, bitrate: 1346 kb/s
    Stream #0.0: Audio: wmav2, 44100 Hz, stereo, s16, 128 kb/s
    Stream #0.1: Video: wmv2, yuv420p, 720x300, 1177 kb/s, 29.97 tbr, 1k tbn, 1k tbc
Output #0, mpegts, to 'BMW.ts':
    Stream #0.0: Video: wmv2, yuv420p, 720x300, q=2-31, 1177 kb/s, 90k tbn, 1k tbc
    Stream #0.1: Audio: wmav2, 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
[mpegts @ 0x9d0c9a0]dts < pcr, TS is invalid
frame= 3281 fps=2134 q=-1.0 size=   20857kB time=109.05 bitrate=1566.8kbits/s   frame= 5234 fps=2569 q=-1.0 size=   28574kB time=173.97 bitrate=1345.5kbits/s   frame= 6615 fps=2607 q=-1.0 size=   37258kB time=220.31 bitrate=1385.4kbits/s   frame= 8028 fps=2641 q=-1.0 size=   45500kB time=267.35 bitrate=1394.2kbits/s   frame= 8765 fps=2547 q=-1.0 Lsize=   51563kB time=292.43 bitrate=1444.5kbits/s    
video:41781kB audio:4581kB global headers:0kB muxing overhead 11.216906%

---

### Post by Jose Catre-Vandis on 2009-05-22
Try this one:
```
ffmpeg -y -threads 2 -i "input.avi" -ab 128k -b 2500k -r 25 -maxrate 8000k  -bufsize 1000k -vcodec mpeg2video  -s 4cif -acodec  mp2  -map 0:0  -map 0:1  "output.ts"
```

I tested it out on an avi file and it worked well, resultant test file loaded up in ProjectX too.

---

### Post by iwannalearn on 2009-05-23
hi, i am really glad you got it to work, now i know there is light at the end of the tunnel

even though it did not for me.

can you see something?

xxxxxx@desktop:~/Desktop/movie$ ffmpeg -y -threads 2 -i movie.avi -ab 128k -b 2500k -r 25 -maxrate 8000k  -bufsize 1000k -vcodec mpeg2video  -s 4cif -acodec  mp2  -map 0:0  -map 0:1  movie.ts
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
[NULL @ 0x8e9ed70]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8e9ed70]frame skip 8
    Last message repeated 1 times
Input #0, avi, from 'movie.avi':
  Duration: 01:27:27.28, start: 0.000000, bitrate: 1091 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 1:1 DAR 5:4], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
Unknown encoder 'mpeg2video'

---

### Post by Jose Catre-Vandis on 2009-05-23
I think your answer is here

[http://ubuntuforums.org/showthread.php?t=986534](http://ubuntuforums.org/showthread.php?t=986534)

in relation to ffmpeg being stripped of non-free codecs etc. Follow this instructions in the linbk and you should be good to go? :)

---

### Post by iwannalearn on 2009-05-23
:KS  Many Many thanks to Jose Catre-Vandis  :KS

Worked 100%

now how would the string be to display on a 16:9 tv?

ffmpeg -y -threads 2 -i "input.avi" -ab 128k -b 2500k -r 25 -maxrate 8000k  -bufsize 1000k -vcodec mpeg2video  -s 4cif -aspect 16:9 -acodec  mp2  -map 0:0  -map 0:1  "output.ts"


Many thanks again

---

### Post by Jose Catre-Vandis on 2009-05-23
Your added option of "-aspect 16:9" looks OK, according to what I have read up on ffmpeg, however, this might depend on the original aspect and size of the original video, so the output might look "squished" or "stretched" on your TV.

Have a look here: [http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)
and search for the section about cropping, which might eventually get you what you want.

---

