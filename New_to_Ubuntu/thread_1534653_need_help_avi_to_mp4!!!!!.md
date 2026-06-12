---
title: "need help avi to mp4!!!!!"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by owners4life5 on 2010-07-19
hello...

i really really, truly have no clue whatsoever on how to do this... so i need all of the help i can get.... can someone please give me a step-by-step on how to convert .avi's to .mp4's? please help me.... i need to have it done in two days.....

any help is greatly appreciated
thanks

---

### Post by moore.bryan on 2010-07-19
You could install ffmpeg and try
```
ffmpeg -i whatever.avi whatever.mp4
```
If that fails, ```
man ffmpeg
``` can never lead astray.

---

### Post by owners4life5 on 2010-07-19
tried that and i.m very confused....)=

---

### Post by nah40 on 2010-07-19
> **owners4life5 said:**
> tried that and i.m very confused....)=

Try Handbrake.
Google for it.

---

### Post by sandyd on 2010-07-19
> **nah40 said:**
> Try Handbrake.
Google for it.
[s]try avidemux[/s]
edit: WinFF is better. its a gui for ffmpeg

---

### Post by owners4life5 on 2010-07-19
i already tried handbrake... i downloaded winff but on the output format there is no mp4 option?

---

### Post by JustinR on 2010-07-19
Try Avidemux then, its in Ubuntu Software Center and it supports many formats, I believe .mp4 should work fine.

---

### Post by Matt__ on 2010-07-19
this has a nice easy GUI and uses ffmpeg/mencoder in the background.
[**_Mobile Media Converter_**](http://www.miksoft.net/mobileMediaConverterDown.htm)

**supports conversions to and from:**
MP3, WMA, WAV, OGG, MP4, MPEG, AVI, (Flash) FLV and (QuickTime) MOV.

drag and drop the movie you want changed and select the output.

---

### Post by owners4life5 on 2010-07-19
> **Matt__ said:**
> this has a nice easy GUI and uses ffmpeg/mencoder in the background.
[**_Mobile Media Converter_**](http://www.miksoft.net/mobileMediaConverterDown.htm)

**supports conversions to and from:**
MP3, WMA, WAV, OGG, MP4, MPEG, AVI, (Flash) FLV and (QuickTime) MOV.

drag and drop the movie you want changed and select the output.

thats sounds a bit easier... i can handle a command line but i guess i.m just stressed this evening /=... i.ll try this

---

### Post by owners4life5 on 2010-07-19
> **owners4life5 said:**
> thats sounds a bit easier... i can handle a command line but i guess i.m just stressed this evening /=... i.ll try this

of course i had to say that... there.s a problem... i choose ipod/iphone cnversion and i.m given that the conversion failed with a terminal code of this:

```
>> Command executed:
"/opt/MIKSOFT/MobileMediaConverter/lib/mencoder" -v -noskip -mc 0 -vfm ffmpeg -vf scale=480:320,harddup -ovc lavc -oac lavc -lavcopts vglobal=1:vcodec=mpeg4:vbitrate=700:autoaspect:aglobal=1:acodec=libfaac:abitrate=128 -of lavf -lavfopts format=ipod -o "/home/brian/Videos/Napoleon Dynamite.mp4" "/home/brian/Videos/Napoleon Dynamite.avi"

>> Result: 
/opt/MIKSOFT/MobileMediaConverter/lib/mencoder: error while loading shared libraries: liba52-0.7.4.so: cannot open shared object file: No such file or directory
----------------------------

```

---

### Post by BigMeanMikeRich on 2010-07-19
liba52 is your ac-3 library.  You could try reinstalling it by simply 
removing it and installing it again (at your own risk):

```
sudo apt-get remove liba52-0.7.4
sudo apt-get install liba52-0.7.4
```

Just my two cents, but once all the libraries are correctly installed and
things are running smoothly, I find that avidemux is a really nice video
conversion tool, and I have used it a lot in the past to shrink video files
for use online and on portable devices. Hopefully it will treat you well.

If you get any more debugging output, post it all here and we'll do our best
to help you figure this out. It's no fun when these things don't work,
especially when it seems like everything is in place.

---

### Post by owners4life5 on 2010-07-20
i would use avidemux.... but i dont know how... can you give me instructions please?

---

### Post by jtarin on 2010-07-20
[Install VLC. it will do what you want simply.]("http://wiki.videolan.org/Documentation:Streaming_HowTo_New")

---

### Post by JustinR on 2010-07-20
Hi,
yes I can.

So first things first, make sure you have Avidemux installed through the Ubuntu Software Center and then install the plugins for it. The plugin file should be called (a free video editor - GTK Plugins) it shows up when you type Avidemux in the search bar.

So after thats done go to Applications > Sound and Video > Avidemux.
Once Avidemux is open click the large Open button and find your video. Once it's loaded under the Video section (left side of window) choose the codec you want to use (MP4 usually uses MPEG 4). If you aren't sure click the bottom one. Then under audio choose MP3. Under Format choose MP4 and click Save!

If you have any problems post back! Good luck :)

---

### Post by owners4life5 on 2010-07-20
thank you justin... i will try that

---

### Post by jtarin on 2010-07-20
See my edited post above for VLC player.

---

### Post by owners4life5 on 2010-07-20
> **jtarin said:**
> See my edited post above for VLC player.

avidemux is seeming to work now that i know how to use it. thank you though... i.ll let everyone know

---

### Post by JustinR on 2010-07-20
Cool, thats good. Also, I would have never though of using VLC but if Avidemux ends up not working try VLC media player.

---

### Post by BigMeanMikeRich on 2010-07-20
An even quick way to use avidemux to convert from .avi to .mp4
(especially if you are looking to play the resulting mp4 file on
a portable device)

[LIST]
[*] Open your avi file (File > Open)
[*] Use the iPod 5.5G Wizard (Auto > Apple > Apple iPod 5.5G)
[*] In the resulting window, select 640x480 for Resolution
[*] File > Save > Save Video. Enter the name of your new video, making sure it ends in .mp4
[/LIST]
Voila!

---

### Post by seventhsamurai on 2010-07-20
Handbrake is THE simplest way to encode. I run a post production facility and have to deliver material in mp4 format for various clients. I use Handbrake.

Load your avi file in it. Set your parameters as you want and let it encode. It will output the file as an m4v file. Dont get scared. its nothing but an mp4. Just rename it to mp4 and all will be fine.

The even simpler way, if you dont want to deal with setting parameters and so on is to download the free h.264 encoder. Just google search for it. It runs under windows, but you can run it in Ubuntu using Wine and it works just fine.

---

### Post by MrWES on 2010-07-20
Have you tried ffmpeg from the commandline?

```
ffmpeg -i myfile.avi -sameq myfile.mp4
```

Bill

---

### Post by karlm on 2010-09-19
> **MrWES said:**
> Have you tried ffmpeg from the commandline?

```
ffmpeg -i myfile.avi -sameq myfile.mp4
```

Bill

I tried that I just get a screen of info that I don't understand. 

```
xxx@xxx-laptop:~/Downloads$ ffmpeg -i MI2.avi MI2.mp4
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
Input #0, avi, from 'MI2.avi':
  Duration: 02:05:24.31, start: 0.000000, bitrate: 813 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
Output #0, mp4, to 'MI2.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```The only bit I understand is the last line; that I don't have the supported codec needed. However, I'm clueless about installing codecs on linux.

---

### Post by andrew.46 on 2010-09-19
Hi karlm,

The problem is here:

```

    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 32 kb/s
[...]
Unsupported codec for output stream #0.1

```

Your copy of FFmpeg has been deliberately built without mp3 encoding. This can easily be rectified by this page:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

although you might be able to get away with the following:

```
ffmpeg -i MI2.avi -acodec copy -vcodec copy MI2.mp4
```

with your existing FFmpeg and this particular file.

Andrew

---

