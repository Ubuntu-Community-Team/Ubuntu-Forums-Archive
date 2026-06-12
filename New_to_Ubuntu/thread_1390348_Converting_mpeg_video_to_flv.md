---
title: "Converting mpeg video to flv"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by Hutchie81 on 2010-01-25
Hello, I need to convert an mpeg video file to flv because when I upload the mpeg file to youtube the sound quality is terrible (even though the original file sounds great).
It seems I need the FFmpeg program to convert the file, but the problem is I have no idea what I'm doing when it comes to downloading/installing. I've found places to download FFmpeg from, but when I click 'download' I only get the options to save or open with archive manager, neither which give me the program. Argh, why doesn't it just download like I want it to!

I've also tried following instructions for installing it using the command window, but it's just too hard for me, and after entering all the commands I still don't have it.

Any help would be gratefully received. Thank you,
Rob

---

### Post by SuperSonic4 on 2010-01-25
It depends what you want ffmpeg for. There is a repo version but it doesn't like mp3 so you'll need to compile your own version or get libavcodec52-unstripped from medibuntu (or similar).

I take mine from SVN for the newest code

```
#!/bin/bash
cd ~/svn
rm -rf x264/
#
git clone git://git.videolan.org/x264 x264
#
# [I]git pull doesn't work with x264 for reasons I'm yet to understand
#[/I]
#
cd x264
./configure --enable-shared --enable-visualize --enable-pic --enable-pthread --extra-ldflags='-fPIC' --prefix=/usr/local
#
make
sudo make install
#
#
# **The above is to install the latest version of x264 from videolan. Ignore if you don't want it**
#
cd ~/svn/ffmpeg
svn up
#
sudo make uninstall
make clean
#
./configure --prefix=/usr/local --enable-pthreads --enable-libx264 \
--extra-cflags='-fPIC' --enable-libfaac \
--enable-libfaad --enable-encoder=x264 --enable-gpl \
--enable-nonfree --enable-libopencore-amrnb \
--enable-version3 --enable-encoder=libx264 \
--enable-encoder=h264 --enable-libvorbis --enable-libtheora \
--enable-libmp3lame --enable-libx264
#
make
sudo make install
```

---

### Post by Hutchie81 on 2010-01-25
Thanks for the quick reply.
Unfortunately I can only follow about 10% of what you are saying as I am a complete beginner.

In my message it says I want to convert an mpeg video file to .flv format.

---

### Post by Enigmapond on 2010-01-25
I use this simple command in ffmpeg that seems to work well for me....

```
ffmpeg -i *filename.mpeg filename.flv*
```

---

### Post by Hutchie81 on 2010-01-25
Lol I don't have it yet - I'm trying to get it...

---

### Post by Enigmapond on 2010-01-25
```
sudo apt-get install ffmpeg
``` :D

---

### Post by oldgeekster on 2010-01-25
> **Hutchie81 said:**
> Lol I don't have it yet - I'm trying to get it...Sounds to me like you might want to check out [medibuntu]("https://help.ubuntu.com/community/Medibuntu")?

---

### Post by Hutchie81 on 2010-01-25
Thanks for helping me out guys.
I ran sudo apt-get install ffmpeg which worked.

But then I tried the conversion command listed earlier in this thread and I got:

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
finalfinishedyes.mpeg: no such file or directory
robert@robert-laptop:~$ ffmpeg -i finishedfinalyes.mpeg filename.flv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mpeg, from 'finishedfinalyes.mpeg':
  Duration: 00:02:32.73, start: 0.133467, bitrate: 5002 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 7500 kb/s, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 224 kb/s
Output #0, flv, to 'filename.flv':
    Stream #0.0: Video: flv, yuv420p, 720x480 [PAR 8:9 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: adpcm_swf, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[adpcm_swf @ 0x9b9eb40]Sample rate must be 11025, 22050 or 44100
Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height

Could anyone offer any more pointers? I'm getting pretty frustrated!

---

### Post by Enigmapond on 2010-01-25
ok it looks like the bitrate in the audio is 48000 and it should be 44100 which is normal...

try this thread

[http://ubuntuforums.org/showthread.php?t=780487](http://ubuntuforums.org/showthread.php?t=780487)    ...you need to change the audio bitrate...to convert it.

---

### Post by J V on 2010-01-25
[handbrake]("apt://handbrake") ftw :P

---

### Post by Enigmapond on 2010-01-25
same difference...he will still need to adjust the bitrate in the audio to change it to flv or swf and handbreak won't do that....
@OP just so you know...you would still have this problem with that file on a windows system...this isn't just an Ubuntu problem.....(Linux Disclaimer)

---

### Post by Hutchie81 on 2010-01-25
Hi, thanks.
I can't find any information to change the bitrate. Is there a command?

---

### Post by Enigmapond on 2010-01-25
You'll find all you need to know about ffmpeg in 

```
man ffmpeg
```

You will learn the application better if you learn it yourself rather than for me to do the coding for you. I will tell you, this is all possible in ffmpeg. Read the manual towards the end regarding conversion.

Cheers.

---

### Post by Hutchie81 on 2010-01-25
Thanks, I tried to understand how to do it by reading the manual, but it was very technical and I'm afraid I just can't figure out what to do.
This is my usual experience - I come across a simple problem (a video conversion), and come to realise that the solution is beyond my capabilities.

If anyone else can help, I'd be very grateful.

---

### Post by SuperSonic4 on 2010-01-25
[QUOTE= man ffmpeg]```
   Audio Options
       -aframes number
           Set the number of audio frames to record.

       -ar freq
           Set the audio sampling frequency (default = 44100 Hz).

       -ab bitrate
           Set the audio bitrate in bit/s (default = 64k).

       -ac channels
           Set the number of audio channels (default = 1).

       -an Disable audio recording.

       -acodec codec
           Force audio codec to codec. Use the "copy" special value to specify that the raw codec data must be copied as is.

```[/QUOTE]

```
ffmpeg -i file.mpeg -vcodec copy -acodec libvorbis -ac 2 -ar 44100 file.flv
```

---

### Post by FakeOutdoorsman on 2010-01-25
> **Hutchie81 said:**
> Hello, I need to convert an mpeg video file to flv because when I upload the mpeg file to youtube the sound quality is terrible (even though the original file sounds great).
It seems I need the FFmpeg program to convert the file, but the problem is I have no idea what I'm doing when it comes to downloading/installing. I've found places to download FFmpeg from, but when I click 'download' I only get the options to save or open with archive manager, neither which give me the program. Argh, why doesn't it just download like I want it to!

I've also tried following instructions for installing it using the command window, but it's just too hard for me, and after entering all the commands I still don't have it.

Any help would be gratefully received. Thank you,
Rob

YouTube should have no problem with an mp2 sound source, but if you would like to convert the audio and just copy the video (no converting done on the video) here is one way of doing it:

1. Install FFmpeg.  Open a Terminal (Applications -> Accessories -> Terminal) and run the following:
```
sudo apt-get install ffmpeg
```
2. Ubuntu does not include all of the encoders by default, so now you need to install one more package to enable the additional encoders.  If you are using Karmic:
```
sudo apt-get install libavcodec-extra-52
```
If you are using an earlier version of Ubuntu, see:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

3. The FFmpeg command:
```
ffmpeg -i input.mpeg -acodec libmp3lame -ac 2 -ab 192k -vcodec copy output.mkv
```
I just tested this and it worked fine on YouTube.  You may get a *lame: output buffer too small* error, but it can be ignored as the output will play just fine.

---

### Post by NFblaze on 2010-01-25
The original poster might want to try a GUI (aka point and click) frontend for FFMPeg, since he is a bit of a novice. Try [WinFF]("http://winff.org/html_new/downloads.html").

---

