---
title: "screen recorder with sound needed"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by stoppage on 2009-09-13
Hi, Im looking for a screen recording àpp for Ubuntu 8.04. Have tried Wink, but I need something with sound included and it nedds to record in a widely used format (at best Flash). Anybody have any ideas here please?

---

### Post by webwiller on 2009-09-13
I'd need something like this too, and went throuw wink as well, but need audio. 
Nobody has a clue? Please... =)

---

### Post by NCLI on 2009-09-13
How about recordmydesktop?

---

### Post by Tropcon on 2009-09-13
Have you tried gtk-recordMyDesktop? I think that it's right in your add/remove aplications list (at least I know that it is in the Jaunty repository.)

It is highly customizable, and can record audio from just about any device (even JACK.) It only outputs to the .ogg format, so from there I usually use WinFF to convert it to whatever format fits my needs. WinFF can convert files to .flv flash video format.

It's been a while since I've used Hardy, so I don't know if both programs are in your repositorys. However, WinFF is simply a front-end for ffmpeg, so if it's not there, there are other ways to do it.

That's what I would recommend. Hope it works for you.

---

### Post by ashwinhgtx on 2009-09-13
Istanbul.

[http://live.gnome.org/Istanbul#head-a2a04263dfc95b0de16520af52c55cf2ee395b9f](http://live.gnome.org/Istanbul#head-a2a04263dfc95b0de16520af52c55cf2ee395b9f)

---

### Post by Ratscallion on 2009-09-13
Like the others, I recommend gtk-recordmydesktop.. To quickly install it, just open up a Terminal (Applications -> Accessories -> Terminal), type
```
sudo apt-get install gtk-recordmydesktop
``` and press enter.

If the sound doesn't work on there, you could use Sound recorder to record it (whilst playing the video, after recording) and edit it on top of it.

---

### Post by stoppage on 2009-09-13
Thanks a lot for the speedy replies...on my way to trying out &#8222;record my desktop&#8220;.

---

### Post by stoppage on 2009-09-14
When I try to convert .ogg (from RMD) to .flv with..........

ffmpeg -i out2.ogg  -b 128 -s 400x240 -pass 1 -passlogfile log-file output.flv

terminal output reads...

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.

  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr

  libavutil version: 1d.49.3.0

  libavcodec version: 1d.51.38.0

  libavformat version: 1d.51.10.0

  built on Mar 17 2009 21:37:49, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

[theora @ 0xb7e1b9a8]Theora bitstream version 30201

[theora @ 0xb7e1b9a8]544 bits left in packet 81

[theora @ 0xb7e1b9a8]7 bits left in packet 82

Input #0, ogg, from 'out2.ogg':

  Duration: 00:00:58.9, start: 0.066667, bitrate: 1051 kb/s

  Stream #0.0: Video: theora, yuv420p, 1440x896, 15.00 fps(r)

  Stream #0.1: Audio: vorbis, 48000 Hz, stereo, 499 kb/s

Output #0, flv, to 'output.flv':

  Stream #0.0: Video: flv, yuv420p, 400x240, q=2-31, pass 1, 0 kb/s, 15.00 fps(c)

  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 64 kb/s

Stream mapping:

  Stream #0.0 -> #0.0

  Stream #0.1 -> #0.1

[flv @ 0xb7e1b9a8]removing common factors from framerate

[theora @ 0xb7e1b9a8]Theora bitstream version 30201

[theora @ 0xb7e1b9a8]544 bits left in packet 81

[theora @ 0xb7e1b9a8]7 bits left in packet 82

[mp3 @ 0xb7e1b9a8]flv doesnt support that sample rate, choose from (44100, 22050, 11025)

Could not write header for output file #0 (incorrect codec parameters ?)


WinFF plays the file, so does Mplayer. Conversion to .avi is also o.k.
Anybody any ideas?

---

### Post by Ratscallion on 2009-09-14
I'm not too good with ffmpeg... However, if you try opening the .ogg file in, say, kdenlive (a video editor, there's a lot so choose whichever you like) and, without editing, render it as a .flv?

---

### Post by paul.gevers on 2009-09-15
> **stoppage said:**
> 
[mp3 @ 0xb7e1b9a8]flv doesnt support that sample rate, choose from (44100, 22050, 11025)


The answer is right there: choose a sample rate (-ar if I am correct) from the list and add it to the ffmpeg command.

---

### Post by stoppage on 2009-09-15
Choosing sample rate worked but the quality of conversion is a disaster with all three. Conversion to .swf, strangely enough,isn`t too bad on quality, it's only flv that's messed up.Could this be a Ubuntu "Bug"?

---

