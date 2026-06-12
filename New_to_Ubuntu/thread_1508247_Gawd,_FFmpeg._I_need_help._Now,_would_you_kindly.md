---
title: "Gawd, FFmpeg. I need help. Now, would you kindly?"
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Hikayu on 2010-06-12
Ok, so: I bought a new mp4 player. Philips GoGear Vibe (SA2VB, to be exact) and I like the fact that it can watch videos. There were a few test videos on it. So now, being on my amazing do-it-all Ubuntu 10.04, decide "Hell yea, time to watch, llolololol!"

So, on to the part where I am now. I spent 4 hours looking for some helpful converter. I tried around 90+. None works. Yes, I tried avidemux, stop telling me to use that. More than 92% of what I used used FFMPEG. So I thought, "Well, let's just use that then."

Now, I installed the thing that allowed me to use ffmpeg to it's fullest. *libavcodec-extra-52*, I believe.


Now, let me just point out what format I'm trying to acheive:
[IMG]http://img13.imageshack.us/img13/7119/screenshotfq.png[/IMG]

In FFMPEG, it'd be:
```
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Vibe Tutorial.mp4':
  Duration: 00:02:35.80, start: 0.000000, bitrate: 1731 kb/s
    Stream #0.0(eng): Audio: adpcm_ima_wav, 22050 Hz, stereo, s16
    Stream #0.1(eng): Video: mjpeg, yuvj420p, 128x128 [PAR 1:1 DAR 1:1], 30 tbr, 30 tbn, 30 tbc
```



Ok, on to the problem. I got a Youtube Video. I ran this code (In order to achieve to the exact same parameters as the given video):
```
ffmpeg -i Left\ 4\ Dead\ 2\ -\ Intro.flv -s 128x128 -vcodec mjpeg -acodec adpcm_ima_wav -ar 22050 output.mp4
```


But does this work? NO! That's why I'm here!
```
hikayu@lynx:~/Desktop$ ffmpeg -i Left\ 4\ Dead\ 2\ -\ Intro.flv -s 128x128 -vcodec mjpeg -acodec adpcm_ima_wav -ar 22050 finished.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'Left 4 Dead 2 - Intro.flv':
  Duration: 00:02:52.90, start: 0.000000, bitrate: 342 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x226, 278 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 64 kb/s
File 'finished.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'finished.mp4':
    Stream #0.0: Video: mjpeg, yuvj420p, 128x128, q=2-31, 200 kb/s, 90k tbn, 29.92 tbc
    Stream #0.1: Audio: adpcm_ima_wav, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mp4 @ 0x891c5c0]track 1: could not find tag, codec not currently supported in container
Could not write header for output file #0 (incorrect codec parameters ?)
```
:-({|=

---

### Post by Mazin on 2010-06-12
If ffmpeg doesn't support that codec in that container, you could try using mencoder (partially ffmpeg powered) but you might have to do the video and audio separately and then remux them into an mp4.

---

### Post by Hikayu on 2010-06-12
> **Mazin said:**
> If ffmpeg doesn't support that codec in that container, you could try using mencoder (partially ffmpeg powered) but you might have to do the video and audio separately and then remux them into an mp4.

Mencoder and I... You know, don't like each other. Any FFMPEG solution? Mencoder is the last thing I'd want to resort to.

---

### Post by halitech on 2010-06-12
have you tried Handbrake? it defaults to mp4 output and has various settings.

what happens when you try avidemux? I use it all the time and it works great for me.

---

### Post by Hikayu on 2010-06-13
> **halitech said:**
> have you tried Handbrake? it defaults to mp4 output and has various settings.

what happens when you try avidemux? I use it all the time and it works great for me.

I'm trying to replicate the EXACT same options as the example video. Also, as for avidemux, it simply doesn't convert properly. I get no video source and it's interface is simply not intuitive.

I'll try avidemux once more and post the results.

---

### Post by d3v1150m471c on 2010-06-13
```

ffmpeg -i ~/path/to/video -sameq ~/path/of/new/video

```
The container, mp4, cannot use the codec you chose for it. The above command will use ffmpeg defaults but strive to replicate the quality of the original. For higher quality try adjusting things like bitrate, frames per second, ect. ect.

---

### Post by nothingspecial on 2010-06-13
Follow [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") guide then assuming you are converting from avi do this


```
#!/bin/bash

#convert avi to mp4
for f in *.avi 
    do 
    ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
    -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.avi}.mp4" \
    "${f%.avi}.mp4"

done;
```

from the directory the original videos are in. It will convert any avi video in the directory and name it correctly, and (importantly if your mp4 player uses tags) tag the title correctly.

Ok so it`s a lot of codey gobbldygook but it will work.

---

### Post by Hikayu on 2010-06-13
> **Hikayu said:**
> I'm trying to replicate the EXACT same options as the example video. Also, as for avidemux, it simply doesn't convert properly. I get no video source and it's interface is simply not intuitive.

I'll try avidemux once more and post the results.

Avidemux doesn't do the video conversion properly for some reason.

Right I chose the setting "Mjpeg" And the "resize" filter to change the resolution to 128x128

---

### Post by Hikayu on 2010-06-13
> **nothingspecial said:**
> Follow [[COLOR="Magenta"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=786095") guide then assuming you are converting from avi do this


```
#!/bin/bash

#convert avi to mp4
for f in *.avi 
    do 
    ffmpeg -i "$f" -acodec libfaac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 \
    -flags +4mv -trellis 2  -cmp 2 -subcmp 2 -s 320x180 -metadata title="${f%.avi}.mp4" \
    "${f%.avi}.mp4"

done;
```

from the directory the original videos are in. It will convert any avi video in the directory and name it correctly, and (importantly if your mp4 player uses tags) tag the title correctly.

Ok so it`s a lot of codey gobbldygook but it will work.

That's not much code.

***GODDAMN IT*, Why doesn't *ANYONE* read the first post and what I'm trying to achieve???**

---

### Post by Hikayu on 2010-06-13
> **d3v1150m471c said:**
> ```

ffmpeg -i ~/path/to/video -sameq ~/path/of/new/video

```
The container, mp4, cannot use the codec you chose for it. The above command will use ffmpeg defaults but strive to replicate the quality of the original. For higher quality try adjusting things like bitrate, frames per second, ect. ect.

If that was true, how the heck was the example video I was provided able to achieve that?

---

### Post by Hikayu on 2010-06-13
**if nobody is going to read the first post, don't answer.**

---

### Post by Hikayu on 2010-06-13
Bump :(

---

### Post by 3rdalbum on 2010-06-13
The manual may tell you exactly what format you can use. Nautilus/Totem might be telling you incorrect information regarding the video codec that is being used by the test videos.

Generally MP3 players can take H.264 or MPEG-4 video in an AVI or MPEG container. I'd try that first. For kicks, you could try my program Blacklight ([https://launchpad.net/blacklight](https://launchpad.net/blacklight)) and see what happens (you'll probably need to use the 'queue' option and then manually copy the files from ~/.blacklight_queue to your player). Blacklight converts video to a precise format required by Sony Walkmans, but it may work for you with your Phillips player.

---

### Post by FakeOutdoorsman on 2010-06-15
I attempted to find more detailed specifications about this player, but did not find much useful information.  It claimed to support "MP4", but did not go into any more details.  The problem with your command from your first post is the audio format.  I'm not sure what to recommend as an audio codec replacement due to the lack of info about the player.  I've never seen this combination in a MP4 container before.  Can you upload *Vibe Tutorial.mp4*?

Instead of trying to reverse engineer this crappy format, perhpas you can attempt some other formats common among portable devices.  Try this:
```
ffmpeg -i input -vcodec libx264 -vpre slow -vpre baseline -s 128x128 -an -threads 0 output.mp4
```
If that works, then add audio:
```
ffmpeg -i input -vcodec libx264 -vpre slow -vpre baseline -s 128x128 -acodec libfaac -aq 100 -threads 0 output.mp4
```
You will need to enable additional encoders in FFmpeg to encode in these formats.  See [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).

Note that you should change *-vpre slow* to *-vpre hq* if you are using an older FFmpeg.

---

### Post by Hikayu on 2010-06-16
> **FakeOutdoorsman said:**
> I attempted to find more detailed specifications about this player, but did not find much useful information.  It claimed to support "MP4", but did not go into any more details.  The problem with your command from your first post is the audio format.  I'm not sure what to recommend as an audio codec replacement due to the lack of info about the player.  I've never seen this combination in a MP4 container before.  Can you upload *Vibe Tutorial.mp4*?

Instead of trying to reverse engineer this crappy format, perhpas you can attempt some other formats common among portable devices.  Try this:
```
ffmpeg -i input -vcodec libx264 -vpre slow -vpre baseline -s 128x128 -an -threads 0 output.mp4
```
If that works, then add audio:
```
ffmpeg -i input -vcodec libx264 -vpre slow -vpre baseline -s 128x128 -acodec libfaac -aq 100 -threads 0 output.mp4
```
You will need to enable additional encoders in FFmpeg to encode in these formats.  See [HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283).

Note that you should change *-vpre slow* to *-vpre hq* if you are using an older FFmpeg.

Your command might probably work. However:

```
File for preset 'slow' not found
```

And when I remove "-vpre slow", I get:

```
[libx264 @ 0x9832790]broken ffmpeg default settings detected
[libx264 @ 0x9832790]use an encoding preset (vpre)
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

Even removing "-vpre baseline" gives the same thing. :(

---

### Post by Hikayu on 2010-06-16
**"Note that you should change -vpre slow to -vpre hq if you are using an older FFmpeg."**

I didn't see that. -_-"

It works. :P. Encoding. I'll post something if it works.

---

### Post by Hikayu on 2010-06-16
Sadly, life isn't easy. It does NOT work.

:-({|=

As for the Video file, I'm afraid that my ISP doesn't care about upload speeds. My upload speed is only 16kb/s. It'd take 30 mins to upload that video. I hope what little information I've given you shall be enough.

---

### Post by ginjabunny on 2010-06-22
I have used ffmpeg to re-encode flv and wmv to avi video using xvid codec (which I beleive is mp4) with audio to mp3. to do this first I used synaptic to install the following 

libavcodec-unstripped-52 (will remove libavcodec52)
libavutil-unstripped-49 (will remove libutil49)

which adds extra codecs

then I run something like one of these below...

ffmpeg -i IN.wmv -acodec libmp3lame -ab 128K -vcodec libxvid -aspect 1.36 -r 25 -b 1500k OUT.avi
or
ffmpeg -i IN.wmv -acodec libmp3lame -ab 128K -vcodec libxvid -aspect 1.777 -r 29.97 -qscale 3 OUT.avi
 
you have to specify apsect for some reason and r (frame rate) should match the original, either use b for bitrate or qscale for quality, if you want to just do a quick test add -vframes 1000 and it will stop after 1000 frames and you can see what you get.

If you do ffmpeg -formats it will list everything it will D decode and E encode, some of the codecs are not what you might think, like mp3 is libmp3lame and xvid is libxvid. I've not tried H264 but it looks like you just specify -vcodec libx264.

Hope this helps

_!!_

---

### Post by MakzieMie on 2010-12-08
Hi Hikayu,
Just curious; did you ever find the answer to your queste?
Thanx,
Erik

---

### Post by Martin Pulec on 2010-12-28
If you are still curious about the answer, this might help (and maybe to the others), at least for my device, which is GoGear VIBE 4GB (or so):

mencoder -of lavf -lavfopts format=mov -oac lavc -vf scale=128:-2 -ovc lavc -lavcopts acodec=adpcm_ima_wav:vcodec=mjpeg in.mpg -o out.mp4 -ofps 30

EDIT: sorry, it is still not fully functional (althoug codecs, resolution and container are good). If I find the final solution, I'll post it.

---

### Post by balasarius on 2011-08-02
Hi had this problem after updating ffmpeg.  where you have -vpre slow check your preset files. I believe to naming has change as part ofthe update. it gets it's slow name from the file name.

example:

the vpre name comes from the part between the "-" and "." inthe filename so...
> 
"libx264-slow.ffpreset" = -vpre slow
"libx264-max.ffpreset" = -vpre max
"libx264-fast.ffpreset" = -vpre fast
And so on...

After the update of ffmpeg I checked the preset files and "libx264-slow.ffpreset" was missing but "libx264-lossless_slow.ffpreset" had replaced it.

so if you check your file presets it will most likey be the same. 
try -vpre lossless_slow and see if it lets you do it.

---

### Post by fredh027 on 2011-12-15
Hello,
I have the same MP4 player.
You should try:
ffmpeg -i "sourcefile.avi" -f mov -vcodec mjpeg -s 160x128 -b 500k -r 24 -acodec adpcm_ima_wav -ab 192k -ar 22050 "targetfile.mp4"
fh

---

### Post by Cpierce on 2011-12-15
Since I am not that good with the command line for converting, I use the GUI for ffmpeg called Winff. If that doesn't work, then I run "Adapter" in a windows VB machine. I also have Arista installed but haven't used it very much.

---

