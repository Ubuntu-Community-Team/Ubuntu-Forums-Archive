---
title: "Avi to Ogg theora"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by rsiddharth on 2009-08-07
How do I convert a .avi file to Ogg Theora ?? . The file that I have to convert is 600MB in size and its certainly not possible for me to convert it in the cloud . 


Thanks for your Help !! . :D

---

### Post by nateperson on 2009-08-07
Top 2 google results.

[https://answers.launchpad.net/ubuntu/+question/13928]("https://answers.launchpad.net/ubuntu/+question/13928")

[http://ubuntuforums.org/archive/index.php/t-481778.html]("http://ubuntuforums.org/archive/index.php/t-481778.html")

---

### Post by andrew.46 on 2009-08-07
Hi rsiddharth,

> **rsiddharth said:**
> How do I convert a .avi file to Ogg Theora ?? . The file that I have to convert is 600MB in size and its certainly not possible for me to convert it in the cloud . 

As some of the posts that nateperson has pointed to suggest FFmpeg would be your best bet. The easiest way may be to to install the repository FFmpeg and also have a look at this:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

which will unlock some of the codecs removed in a default Ubuntu installation. FFmpeg can be a bit confusing if you have not used it before so if you have trouble could you post the results of:
```

ffmpeg -i *[COLOR="Red"]myfile[/COLOR]*.avi
```

here and I am sure the most correct syntax can be suggested to you.

All the best,

Andrew

---

### Post by Flimm on 2009-08-07
Install VLC from the repos (Applications, Add/Remove... search for VLC, tick it and click Apply changes).
Open VLC media player. Click Media, Convert/Save. Add the file you want to convert. Click Convert/Save. Choose a destination file, with the extension .ogv . Under profile, choose "Video - Theora + Vorbis (OGG)". Click Start. The conversion will be finished as soon as the playback slider reaches the end.

---

### Post by LunaticHiatus on 2009-08-07
install ogg converter from add/remove. Its extremely simple to use.

---

### Post by rsiddharth on 2009-08-08
Thank you all for your suggestions and help  !!  .

andrew , I will post the result of the command shortly . 

I was looking at VLC as a prospective converter , Now that Flimm recommends , I will have VLC as an option if ffmpeg fails to work ! . 

I have tried ogg converter before ( though not for .avi --> Ogg theora ) , Its interface is simple and straight forward , but it seems that it converts everything  into .ogg , which I presume is audio only ( correct me if I am wrong ) .

---

### Post by rsiddharth on 2009-08-08
Here is the output that I got for the following command 

The command :
```

 ffmpeg -i yanni_-_live_at_the_acropolis__dvd_.avi

```The output :
```

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

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 29.97 (30000/1001)
Input #0, avi, from 'yanni_-_live_at_the_acropolis__dvd_.avi':
  Duration: 01:36:19.32, start: 0.000000, bitrate: 921 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified

```

---

### Post by andrew.46 on 2009-08-08
Hi rsiddharth,

> **rsiddharth said:**
> 
```

Duration: 01:36:19.32, start: 0.000000, bitrate: 921 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 30k tbc
Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
At least one output file must be specified

```

Oddly enough I had mixed results testing this with a few files on my system with the current svn FFmpeg. But have a try with:

```
ffmpeg -i yanni_-_live_at_the_acropolis__dvd_.avi -vcodec libtheora -b 800k -acodec vorbis -ac 2 -f ogg output.ogv
```

and just check the result carefully. When I converted from a few mp4s (h264 + aac) to ogv the resulting video could not be played. Having read Flimm's thoughts on vlc I tried this on the same files and they were converted effortlessly. First time FFmpeg has let me down :(.

Andrew

---

### Post by rsiddharth on 2009-08-09
Thank you  Andrew it worked for me !! - ffmpeg : 
 
```

ffmpeg -i yanni_-_live_at_the_acropolis__dvd_.avi -vcodec libtheora -b 800k -acodec vorbis -ac 2 -f ogg output.ogv

```It will be great if anybody unravels what the command means , I understand what this means :

```

ffmpeg -i yanni_-_live_at_the_acropolis__dvd_.avi 

```and what this means :
```

 output.ogv

```The code in between is a absolute mystery for me :
```
 
 -vcodec libtheora -b 800k -acodec vorbis -ac 2 -f ogg 

```

-------------
I thank all of you in this thread for helping me out so beautifully and graciously  !!! . I am elated . 
---------

---

### Post by andrew.46 on 2009-08-09
Hi rsiddharth,

> **rsiddharth said:**
> Thank you  Andrew it worked for me !! 

Well I must say I am a little relieved as some of my experimentation with FFmpeg conversions to ogv were a little worrying :-).

> The code in between is a absolute mystery for me :

```
 -vcodec libtheora -b 800k -acodec vorbis -ac 2 -f ogg 
```


It becomes quite straightforward the more you use it and the syntax is actually quite logical:

[LIST]
[*]**-vcodec libtheora**: Simply means use the video codec libtheora
[*]**-b 800k**: libtheora + FFmpeg uses a default bitrate of 200k and I saw that your movie actually had a higher bitrate than that so I specified *-b(itrate) 800k*.
[*]**-acodec vorbis**: Use the audio codec vorbis to process the sound.
[*]**-ac 2**: FFmpeg insists on the audio channels being specified as 2 for this type of encoding
[*]**-f ogg**: This ensures that an ogg container is used. I have a suspicion that FFmpeg might do that anyway based on the .ogv suffix of the output file but I put it in anyway :-).
[/LIST]

A simpler way if you were interested is to use the commandline tool FFmpeg2theora which has the slightly odd idea of using a commandline front for a commandline program!

Andrew

---

### Post by rsiddharth on 2009-08-09
Thank you Andrews for making me aware of the intricacies of the command . I came across FFmpeg2theora in few sites which I searched for(Wikimedia Commons-http://commons.wikimedia.org/wiki/Help:Converting_video,etc) before starting this thread . I presume we got to convert the required file into mpeg before being able to ultimately converting it to theora ( correct me if my idea of it wrong ) .

---

### Post by andrew.46 on 2009-08-09
Hi rsiddarth,

> **rsiddharth said:**
> I came across FFmpeg2theora in few sites which I searched for(Wikimedia Commons-http://commons.wikimedia.org/wiki/Help:Converting_video,etc) before starting this thread . I presume we got to convert the required file into mpeg before being able to ultimately converting it to theora ( correct me if my idea of it wrong ) .

I have not used FFmpeg2theora widely but I believe it will actually handle any input files that FFmpeg itself can handle so no conversion should be necessary. Just to reacquaint myself with the program I ran it across a Rammstein mp4 I had available and it runs *very* nicely:

```

$ ffmpeg2theora -v 8 -a 6 Rammstein_Mutter.mp4 --no-skeleton --optimize -o rammstein.ogv
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Rammstein_Mutter.mp4':
  Duration: 00:03:45.90, start: 0.000000, bitrate: 338 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, 2 channels, s16
    Stream #0.1(und): Video: h264, yuv420p, 352x264 [PAR 1:1 DAR 4:3], 24.99 tbr, 24991 tbn, 49982 tbc
  Pixel Aspect Ratio: 1.00/1   Frame Aspect Ratio: nan/1
  Resize: 352x264
      0:03:45.88 audio: 202kbps video: 261kbps, time elapsed: 00:02:52  

```

You will note of course that there is a new set of commandline options to learn :-).

Andrew

---

### Post by rsiddharth on 2009-08-10
Thank you for the Information Andrew ! . 

> 
You will note of course that there is a new set of commandline options to learn :smile:.
I always had something to learn since i installed jaunty ( my first GNU/Linux Distro ) and it seems to me that never finish &quot; learning &quot; or can be called a &quot; pundit &quot; since there is always something new and interesting  coming up .

---

