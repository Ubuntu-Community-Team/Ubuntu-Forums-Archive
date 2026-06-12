---
title: "ffmpeg flv conversion trouble"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by moose12 on 2009-04-15
im trying to get a flv file converted to mpg through use of ffmpeg but i continue to get an error stating "Unsupported video codec (7)"

so i seems i dont have the codec needed but i also cant seem to find it. help please?

---

### Post by FakeOutdoorsman on 2009-04-15
You probably need to enable the restricted encoders:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Also show your FFmpeg command, the full FFmpeg output, and your Ubuntu version.

---

### Post by moose12 on 2009-04-15
[flv @ 0x7f22f1615040]Unsupported video codec (7)
[flv @ 0x7f22f1615040]Unsupported video codec (7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/nathan/Videos/lucky.flv':
  Duration: 00:03:18.7, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: 0x0007, 25.00 tb(r)
    Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
File 'lucky.mpg' already exists. Overwrite ? [y/N] y
swScaler: Unknown format is not supported as input format
Cannot get resampling context


the unsupported line does that alot i only copied two of them
and im runnin intrepid ibex 64bit

---

### Post by FakeOutdoorsman on 2009-04-15
What is the command you are giving FFmpeg to convert the video?

---

### Post by HotForLinux on 2010-03-03
$ffplay cannonball.flv

Error Output:
[flv @ 0xb7edf110]Unsupported video codec (7)
[flv @ 0xb7edf110]Unsupported audio codec (a)
[flv @ 0xb7edf110]Unsupported video codec (7)
.....
[flv @ 0xb7f73110]Unsupported video codec (7)
[flv @ 0xb7f73110]Unsupported video codec (7)
cannonball.flv: could not open codecs

I have the Medibuntu ffmpeg package installed in Hardy Heron.
Where are the flv codecs for Hardy??

---

