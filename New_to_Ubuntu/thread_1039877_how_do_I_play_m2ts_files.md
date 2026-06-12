---
title: "how do I play m2ts files?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by chilimac02 on 2009-01-15
I want to play the files straight from my camcorder in m2ts format. I do not want to convert them first - something is always lost in conversion. There has to be a codec or something I can install. Any ideas?

-Justin
BTW ubuntu 8.10

---

### Post by mcduck on 2009-01-15
Actually if you convert from MPEG2 Transport Stream to normal MPEG2, nothing gets lost in the conversion. And it will only take a couple of minutes for a full-length movie.

The video format is basically the same, so there's no need to re-compress the video. It's just a simple change in the file's data structure.

But if you want to play MPEG2 TS files, give VLC a try.

---

### Post by chilimac02 on 2009-01-19
So, which program do I use to convert to Mpeg2?
I've tryed VLC for my m2ts, it's really buggy (video and sound not synchronized and only part of video displayed...)

-Justin

---

### Post by fuser312 on 2009-01-19
Kaffeine : to play your m2t format

---

### Post by mcduck on 2009-01-19
That is likely to happen if there is even one bug in the transport stream.

I have a Mac for video editing so I've been using MPEG Streamclip for this purpose, but sadly there's no Linux version. ProjectX has a Linux version (available in Ubuntu's repositories) and is specifically made for this purpose. You could give it a try..

(Avidemux definitely can do it, but it doesn't automatically fix errors in the stream which means that you'd need to convert a short clip, estimate the delay between sound and video, set the correction in Avidemux and then convert the whole file.)

---

### Post by stefangr1 on 2009-01-19
> **chilimac02 said:**
> I want to play the files straight from my camcorder in m2ts format. I do not want to convert them first - something is always lost in conversion. There has to be a codec or something I can install. Any ideas?

-Justin
BTW ubuntu 8.10

You don't have to convert them. You can just rename them to .ts such that mplayer and vlc know what to do with them, and than they should play. I'm quite sure at least mplayer plays them.

---

### Post by savior02 on 2009-10-31
> **fuser312 said:**
> Kaffeine : to play your m2t format

thanx!

---

### Post by savior02 on 2009-10-31
> **fuser312 said:**
> Kaffeine : to play your m2t format

actually i just tried it and it doesnt play..any ideas?

---

### Post by bigspottycat on 2009-10-31
I use VLC which plays these M2TS (AVCHD) fine, without any need to convert them. However, you need a reasonably powerful processor to play them smoothly. If they are skipping, there is an option to skip frames to make them play more smoothly.

Good luck.

---

### Post by savior02 on 2009-10-31
> **bigspottycat said:**
> I use VLC which plays these M2TS (AVCHD) fine, without any need to convert them. However, you need a reasonably powerful processor to play them smoothly. If they are skipping, there is an option to skip frames to make them play more smoothly.

Good luck.

thanx it worked!where is that option??

---

### Post by bigspottycat on 2009-11-01
Glad to hear it worked. The option to skip frames helped reduce skipping for me:

If you are using VLC 1.02 (GoldenEye) go to Tools-Preferences, then click on the Show Settings-All (radio button). Under Input/Codecs-Other Codecs-FFmpeg make sure the 'Skip the Loop Filter for h.264 decoding' option is set to 'All'. There is also an option under Input/Codecs-Video Codecs-x264 for 'Skip loop filter' which is not ticked by default. I don't know whether this makes any difference. If you have changed any options, click Save.

If you are getting lots of horizontal lines on the video, you need deinterlace (Video-Deinterlace-Bob).

Hope this works.

---

### Post by Francewhoa on 2010-03-13
Installing the latest version of VLC worked for me. To do so following instructions at [http://ubuntumanual.org/posts/195/install-all-new-vlc-1-0-in-ubuntu-jaunty-intrepid-hardy](http://ubuntumanual.org/posts/195/install-all-new-vlc-1-0-in-ubuntu-jaunty-intrepid-hardy)

---

### Post by chuck_d on 2010-05-07
> **bigspottycat said:**
> Glad to hear it worked. The option to skip frames helped reduce skipping for me:

If you are using VLC 1.02 (GoldenEye) go to Tools-Preferences, then click on the Show Settings-All (radio button). Under Input/Codecs-Other Codecs-FFmpeg make sure the 'Skip the Loop Filter for h.264 decoding' option is set to 'All'. There is also an option under Input/Codecs-Video Codecs-x264 for 'Skip loop filter' which is not ticked by default. I don't know whether this makes any difference. If you have changed any options, click Save.

If you are getting lots of horizontal lines on the video, you need deinterlace (Video-Deinterlace-Bob).

Hope this works.

Thanks.  This worked for me.  It's worth noting that it will degrade the quality of the image, but if your hardware cannot support playback of the video file, then what else are you going to do?

One note: ALL is the lowest image quality setting.  First try Non-ref, if that doesn't work then Non-key, at least that way you're still pulling full key frames which should be almost the same as All in terms of performance.

---

### Post by tsx2424 on 2011-03-01
I set the Non-ref and It nothing changed.I trying to convert to .avi with using mencoder.but it doesnt work.maybe  the file is corrupted. Thank you for helping.

---

### Post by tsx2424 on 2011-03-02
I'm used Avidemux as saved from m2ts to avi.although it is unwatchable.so Im used mencoder and It works.Quality is almost same as m2ts.

---

### Post by stephenbbb on 2012-01-01
I have VLC 1.12 on Ubuntu 11.10 and it cannot play the m2ts.

mplayer plays it very bad. it is annoying that windows media player in win 7, which is about 5 times slower than Ubuntu plays the files without a hiccup. definitely a codec issue, not processor.

Please, advise if there is a solution.

---

### Post by Jerry N on 2012-01-02
I had the same issue with my Canon Camcorder videos using a GT9800 video board, an Athlon 3800 (dual core, 2mhz clock) and 2gb RAM.  Worked perfectly with the Win 7 Media player but very poorly with every Linux video player I tried.  Then my motherboard died and I replaced it with a quad core Phenom II 965 system with 4gb RAM.  Using the same video board, I now get excellent performance with VLC with both 32 bit and 64 bit Ubuntu derivatives.  Right now I am using Mint 11.  Conclusion:  Win 7 is more efficient at playing videos than Linux but if you have a big honkin' Linux machine it doesn't make any difference.

Jerry

PS I just noticed that this is a very old thread.

---

### Post by manustays on 2012-01-07
> **stephenbbb said:**
> I have VLC 1.12 on Ubuntu 11.10 and it cannot play the m2ts.

mplayer plays it very bad. it is annoying that windows media player in win 7, which is about 5 times slower than Ubuntu plays the files without a hiccup. definitely a codec issue, not processor.

Please, advise if there is a solution.

Same problem here. Cannot play m2ts files with VLC 1.1 on Ubuntu 11.10. Considering this thread is very old, it did seem to play well with VLC before!

---

### Post by stephenbbb on 2012-01-13
Gurus:

please, advise how to play m2ts files on ubuntu 11.10. codec is recognized correctly in vlc. hardware: acer 5250 dual core athlon with 2gb ddr3 and radeon HD6250.
is it possible the radeon driver is old and causing the problem??
works great in windows :-(

---

