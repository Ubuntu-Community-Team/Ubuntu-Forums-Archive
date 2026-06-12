---
title: "Pitivi won't encode to h.264 MP4. . ."
date: 2010-05-09
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2010-05-09
Hi.  I've been trying to re-encode some videos from various formats to h.264, AAC, MP4 files with PiTiVi.  This worked perfectly until I upgraded to 10.04, this system has been upgraded all the way up from 6.10.  I have the good, bad, and ugly sets of gstreamer plugins installed, and all the stuff from ubuntu-restricted-extras.  The encoding status windows appears, and it says "Rendering" in the status bar, but it never advances, and there is no additional CPU usage.  I've reinstalled all these plugins, Pitivi, and used other versions of PiTiVi, older and newer, compiled from source.  I've tried converting from ogg, avi, etc, to no avail.  I've tried the FFmpeg and FLV muxers as well, x264enc is definitely the problem. . . 

Any ideas?

Thanks in advance.

P.S. I've tried LIVES and Avidemux too, neither worked.  However, the Arista Transcoder works, but it doesn't give me enough control over the conversion. . .

---

### Post by 3rdalbum on 2010-05-09
There's a set of packages whose names start with "libav" and end in the word "extra" and a number. These give restricted format support to FFMPEG and will be used by Pitivi and most video editors and transcoders.

There's "libavcodec", "libavformat", "libavdevice" and others, but if you just search for "libav" you'll find them. Remember you need the packages with the word "extra" in their names.

---

### Post by pi.boy.travis on 2010-05-09
Installed libav*-extra-52 packages, but it still stalls with none of the video rendered.  No error anywhere. . .  I booted up a live USB, installed the restricted extras, and couldn't encode the video with that either, so it must be a bug somewhere.  I've read that the fluendo plugins cause issues, but I don't have any installed. . . 

Anything else I can do?

---

### Post by pi.boy.travis on 2010-05-09
I think I found a bug report: [https://bugs.launchpad.net/ubuntu/+source/pitivi/+bug/503937](https://bugs.launchpad.net/ubuntu/+source/pitivi/+bug/503937)

---

### Post by skatebiker on 2010-05-10
Same issue with my pitivi, but also with KDEnlive which both make use of ffmpeg which also cannot encode h.264 since 10.04.

---

### Post by nikhilbhardwaj on 2010-05-10
the ffmpeg version that comes with ubuntu is stripped down due to licensing restrictions
if you compile it from source then it should work
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Paqman on 2010-05-10
> **nikhilbhardwaj said:**
> the ffmpeg version that comes with ubuntu is stripped down due to licensing restrictions
if you compile it from source then it should work
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

I'd try the Medibuntu packages before getting into compiling an important part of the system.

---

### Post by pi.boy.travis on 2010-05-10
Installed the Medibuntu codecs, still no good.  I'd rather not compile from source, as it makes it difficult to remove later.  Maybe I'll try packaging it later.  Anything else I can do?

---

### Post by pi.boy.travis on 2010-05-10
It's definitive, Ubuntu 10.04 can't encode h.264.  I've tried it on six computers now, all of them could do it in 9.10.  Compiling is all I haven't tried.  I hope this has nothing to do with Canonical licensing h.264 for OEMs. . . 

If anyone finds another way to get it working, so share.

---

### Post by aaguilar4 on 2010-05-20
Just as a confirmation I'd like to state that I installed everything from the repositories rather than compiling myself and found that when running 'ffmpeg -formats' from the command line, it said that it couldn't Encode in the h.264, only decode.
I don't remember if it was this way for older versions of ubuntu, but I believe it wasn't. Any solutions that don't include compiling the package with different configurations?

---

### Post by dannyboy79 on 2010-06-15
well, i just issued ffmpeg -formats and I see this:
DE h264            raw H.264 video format
D means decode and E means encode doesn't it? I did compile ffmpeg myself awhile back. version is this: 

FFmpeg version SVN-r23034, Copyright (c) 2000-2010 the FFmpeg developers
  built on May  6 2010 10:55:53 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab

Anyway, my point is that i have tried to use the settings in Pitivi and it says x264, not h264 so my render in pitivi just sits there and doesn't move, and also cpu doesn't move so I am not sure how to use pitivi to encode a raw dv file into a h264 file for youtube. any help please? I have tried handbrake (don't think it accepts dv files from kino), i have tried kdenlive and i don't see an option to export a h264 or x264 from kino, only xvid i think? i am trying to capture xbox 360 game play through firewire (analog from thru a dazzle hollywood dv bridge) and then trying to edit and add animation in linux tools, then export for upload to youtube. I was doing this is iMovie HD and everything was so easy but my dad took his powerbook g4 back. DAMN IT. Anyone, pelase help.

---

### Post by no2498 on 2010-06-15
seen the h264 install as i installed smplayer

hope this helps

---

### Post by Irony on 2010-06-15
Pitivi doesn't work for me in Lucid (did in Karmic) though Avidemux does, so maybe try Avidemux.

---

### Post by dannyboy79 on 2010-06-15
h264enc is the package name, i just found it and installed it but when I run this command:```
ffmpeg -f dv -i capture008.dv -acodec aac -vcodec h264 -s 720x480 -aspect 4:3 capture008.mp4
``` it still says unknown encoder h264, tried h264enc, failed, tried x264, failed.

---

### Post by no2498 on 2010-06-16
try a diff size like 640x480
this does not look right 720x480 

hope that helps

---

### Post by fallenshadow on 2010-06-16
I had this exact same problem... seems like its not available for some reason.

---

### Post by dannyboy79 on 2010-06-17
> **no2498 said:**
> try a diff size like 640x480
this does not look right 720x480 

hope that helps

> **no2498 said:**
> try a diff size like 640x480
this does not look right 720x480 

hope that helps

size wouldn't have anything to do with codec. it turns out it's written like this

```
ffmpeg -i INPUT -acodec libfaac -ab 128k -ac 2 -f mp4 -vcodec libx264 -vpre slow -crf 25 -s 480x360 -deinterlace -threads 0 OUTPUT.mp4
```
notice the libx264, not h264 or x264.
we'll see how it turns out. im trying to find the best settings for decent amount of time for encoding and good quality for youtube.

---

### Post by dannyboy79 on 2010-06-25
ok. for some reason i can't export in pitivi using anything that uses libx264, i ahve tried in a avi container, a mp4 container, i have tried ac3 audio, mp3 audio to no avail. it just sits there at the render progress and it never moves. any thoughts? i ahve compiled ffmpeg against svn and git as well as x264. i couldn't get --enable-shared to work so i just compiled it static. any thoughts why i can't export from pitivi using x264? i have tried openshot and I don't think that works either, only xvid. here is my ffmpeg info

 ffmpeg -version
FFmpeg version SVN-r23789, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jun 25 2010 14:15:02 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.19. 0 / 50.19. 0
  libavcodec    52.78. 0 / 52.78. 0
  libavformat   52.71. 0 / 52.71. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.20. 0 /  1.20. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
FFmpeg SVN-r23789
libavutil     50.19. 0 / 50.19. 0
libavcodec    52.78. 0 / 52.78. 0
libavformat   52.71. 0 / 52.71. 0
libavdevice   52. 2. 0 / 52. 2. 0
libavfilter    1.20. 0 /  1.20. 0
libswscale     0.11. 0 /  0.11. 0
libpostproc   51. 2. 0 / 51. 2. 0

---

### Post by stmiller on 2010-06-26
See this: [http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

tl;dr - you need medibuntu

---

### Post by tylerious on 2010-07-20
I have the same problem. I can "Render" in Pitivi with other codecs, but not "x264enc".

I tried Medibuntu, and although that listed libx264 as supporting encoding, I still cannot render in Pitivi.

I tried compiling x264 and ffmpeg from source following the link posted here, and although that also lists libx264 as supporting encoding, I still cannot render in Pitivi.

Is this because Pitivi is trying to use x264enc, not libx264? Command `ffmpeg -codecs` results:

"D V D  h264            H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10
  EV    libx264         libx264 H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10"

It sounds like one needs to specify "libx264" when using ffmpeg to encode h.264, not "x264" or "h264". Does Pitivi just not know this?

---

### Post by tylerious on 2010-07-21
I have submitted a new bug to PiTiVi:

[https://bugzilla.gnome.org/show_bug.cgi?id=624931](https://bugzilla.gnome.org/show_bug.cgi?id=624931)

---

### Post by Threevolve on 2012-09-03
1. Install medibuntu repos
2. apt-get install ubuntu-restricted-extras
3. search repos for "unstripped"; install all of the ffmpeg unstripped libs
4. Pitivi now renders AAC/x264

---

