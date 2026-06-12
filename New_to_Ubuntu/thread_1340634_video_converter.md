---
title: "video converter"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by patchido on 2009-11-28
well, i was wondering what program could i use to convert all kind of video,(rm, avi, mpg) into ipod format??

---

### Post by jamieleshaw on 2009-11-28
Hello, arista transcoder is one
sudo apt-get install arista

---

### Post by MichaelFTW on 2009-11-28
Try WINFF, it's probably the easiest. (IMO)
[http://winff.org/html_new/](http://winff.org/html_new/)          :D

---

### Post by 3rdalbum on 2009-11-28
Here's the rough thing: Ubuntu 9.10 doesn't have AAC audio encoding because of a licensing problem. AAC is the audio format used in iPod videos. WinFF and Arista depend on a library called FFMPEG that does the transcoding for them; and it's this library that (in Ubuntu 9.10's configuration) does not include AAC encoding.

You can get around this by compiling your own copy of FFMPEG, which will override the system copy:

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

There doesn't seem to be an easier way, sorry. Unless you want to install Ubuntu 9.04 onto your computer or into a virtual machine, because 9.04 still includes AAC encoding.

---

### Post by michaelzap on 2009-11-28
> **3rdalbum said:**
> Here's the rough thing: Ubuntu 9.10 doesn't have AAC audio encoding because of a licensing problem.

...

There doesn't seem to be an easier way, sorry. Unless you want to install Ubuntu 9.04 onto your computer or into a virtual machine, because 9.04 still includes AAC encoding.

Actually, I think that's incorrect. I'm running Karmic with the "unstripped" codecs from the Mediabuntu repos, and I can encode to AAC audio just fine. I just did it now to make sure that I wasn't crazy, and it worked with no problems at all.

I highly recommend Handbrake to convert to h.264 format (which is perfect for iPods) - it blows WinFF, AviDemux, and everything else away (for this format).

---

### Post by 3rdalbum on 2009-11-29
> **michaelzap said:**
> Actually, I think that's incorrect. I'm running Karmic with the "unstripped" codecs from the Mediabuntu repos, and I can encode to AAC audio just fine. I just did it now to make sure that I wasn't crazy, and it worked with no problems at all.

Interesting. At one point in time it was disabled due to a licensing problem, and my Blacklight script wouldn't work. I don't remember seeing any FFMPEG updates come down the line either... interesting.

---

### Post by bumanie on 2009-11-29
> I highly recommend Handbrake to convert to h.264 format
I read that handbrake is not working in 9.10 - can't confirm or deny from personal experience, but read the same thing twice from different places. Winff does adequate conversions to h.264 as far as I know.

---

### Post by michaelzap on 2009-11-29
> **bumanie said:**
> I read that handbrake is not working in 9.10 - can't confirm or deny from personal experience, but read the same thing twice from different places. Winff does adequate conversions to h.264 as far as I know.

That was before the latest Handbrake was released (0.94):
[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

---

### Post by kevdog on 2009-11-29
+1 on Handbrake -- and if you really run into a bind you could compile it from source.  There are instructions on the Handbrake page that actually are very complete and work relatively well.  I even cross-compiled the latest svn release on Ubuntu for Windows using mingw -- so it definitely works!!

---

### Post by FakeOutdoorsman on 2009-11-30
> **michaelzap said:**
> Actually, I think that's incorrect. I'm running Karmic with the "unstripped" codecs from the Mediabuntu repos, and I can encode to AAC audio just fine. I just did it now to make sure that I wasn't crazy, and it worked with no problems at all.

I highly recommend Handbrake to convert to h.264 format (which is perfect for iPods) - it blows WinFF, AviDemux, and everything else away (for this format).

There are no unstripped FFmpeg libraries offered by Medibuntu for Karmic as far as I know.  The *non-free-codecs* package has *ubuntu-restricted-extras* as a dependency, but currently *ubuntu-restricted-extras* does not install the "unstripped" or "extra" packages.  Did you mean the *libavcodec-extra-52* package available in the Ubuntu multiverse repository?

I am curious how you got the Karmic FFmpeg to encode to AAC.  Perhaps I am behind the times.  Can you show your FFmpeg command and the complete FFmpeg output?

---

### Post by michaelzap on 2009-11-30
> **FakeOutdoorsman said:**
> There are no unstripped FFmpeg libraries offered by Medibuntu for Karmic as far as I know.  The *non-free-codecs* package has *ubuntu-restricted-extras* as a dependency, but currently *ubuntu-restricted-extras* does not install the "unstripped" or "extra" packages.  Did you mean the *libavcodec-extra-52* package available in the Ubuntu multiverse repository?

I am curious how you got the Karmic FFmpeg to encode to AAC.  Perhaps I am behind the times.  Can you show your FFmpeg command and the complete FFmpeg output?

Hmm... Well I suppose I just assumed that the unstripped libavcodec package came from Mediabuntu (since I have those repos enabled). I do have the libavcodec-extra-52 package installed also.

And I actually didn't test AAC encoding using FFmpeg but rather using Handbrake. I could test it out and see what happens. I would think that if Handbrake can do it then FFmpeg ought to be able to do it also, but perhaps not.

---

### Post by michaelzap on 2009-11-30
> **michaelzap said:**
> And I actually didn't test AAC encoding using FFmpeg but rather using Handbrake. I could test it out and see what happens. I would think that if Handbrake can do it then FFmpeg ought to be able to do it also, but perhaps not.

Nope.
```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1
[NULL @ 0x2047280]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from '/home/zap/Desktop/lucio6-024.avi':
  Duration: 00:00:09.45, start: 0.000000, bitrate: 1937 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 720x480 [PAR 32:27 DAR 16:9], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 160 kb/s
Unknown encoder 'libfaac'
Press Enter to Continue  


```
So I guess Handbrake is the way to go for now.

---

### Post by VertexPusher on 2009-11-30
> **3rdalbum said:**
> Ubuntu 9.10 doesn't have AAC audio encoding because of a licensing problem.
Ubuntu 9.10 provides at least four ways to encode AAC:
[list][*]Avidemux[*]MEncoder[*]GStreamer[*]FAAC command line encoder[/list]
These four tools work out of the box, without any 3rd party repositories. Why would anyone want to use FFMPEG anyway?

---

### Post by 3rdalbum on 2009-11-30
> **VertexPusher said:**
> Ubuntu 9.10 provides at least four ways to encode AAC:
[list][*]Avidemux[*]MEncoder[*]GStreamer[*]FAAC command line encoder[/list]
These four tools work out of the box, without any 3rd party repositories. Why would anyone want to use FFMPEG anyway?

Lots of programs already depend on FFMPEG.

Mencoder is a bit complex for me, and frankly Gstreamer is severely challenged in terms of input format support.

---

### Post by VertexPusher on 2009-11-30
> **3rdalbum said:**
> Lots of programs already depend on FFMPEG.
Yes, but doing AAC or H.264 encoding through libavcodec is just not a very bright idea. Even if it works, most of the advanced x264 and FAAC settings are not accessible.

> Mencoder is a bit complex for me
At least it comes with proper documentation of all the command line options. With FFMPEG you are always guessing: Does this option apply to that encoder at all? FFMPEG's approach is to map all codecs to the same set of command line options, and that just doesn't work in many cases. Even if two codecs support the same option, the range of values may be different. Example: quantizer in Xvid vs. quantizer in x264.

> frankly Gstreamer is severely challenged in terms of input format support.
Its input format support is at least on par with FFMPEG. That's not surprising since FFMPEG is available as a GStreamer plugin. Maybe you forgot to install it?

---

### Post by 3rdalbum on 2009-11-30
> **VertexPusher said:**
> Yes, but doing AAC or H.264 encoding through libavcodec is just not a very bright idea. Even if it works, most of the advanced x264 and FAAC settings are not accessible.

I don't really care... I just want something simple to use.

> At least it comes with proper documentation of all the command line options. With FFMPEG you are always guessing: Does this option apply to that encoder at all?

I don't have any experience about that sort of thing, but frankly Mencoder's documentation is frighteningly massive. FFMPEG's may be lacking, but it's consise enough.


> Its input format support is at least on par with FFMPEG. That's not surprising since FFMPEG is available as a GStreamer plugin. Maybe you forgot to install it?

I've got it, I always install it. Maybe it's just a Gstreamer problem, because Totem will often refuse to have anything to do with a file that I can play with 'ffplay' or VLC.

---

### Post by VertexPusher on 2009-11-30
> **3rdalbum said:**
> Maybe it's just a Gstreamer problem, because Totem will often refuse to have anything to do with a file that I can play with 'ffplay' or VLC.
Totem plays anything I throw at it: avi, mpg, vob, mp4, mov, mkv, ogg, flv, asf, wmv, wma, mp3, wav, FLAC, Xvid, H.264, AAC, Vorbis, Theora, you name it.

The only exception is RealMedia. But FFMPEG can't handle that either.

I guess there are some plugins missing in your installation. Maybe you installed the plugin sets from universe instead of multiverse.

---

### Post by no2498 on 2010-01-20
i know this tread is old but its my 2 cents try this 1

[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)


it works on 910 and 804

read the page do as he says
 enjoy

---

