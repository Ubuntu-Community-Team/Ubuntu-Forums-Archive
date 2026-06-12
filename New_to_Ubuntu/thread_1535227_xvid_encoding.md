---
title: "xvid encoding"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by aust77 on 2010-07-20
Alright, so I want to record a surveillance video overnight using my Canon PowerShot A470 plugged via AC adapter into the wall and plugged into my computer via USB. Problem is, the video made by the camera is encoded with a different codedc (I'm actually not sure the specific one) that makes the .avi videos far to large. I'm looking for a program that can encode the video into xvid so it won't be an insanely high GB size.


Thanks in advance for any assistance,


aust77

---

### Post by bodhi.zazen on 2010-07-20
ffmpeg will do this for you.

There are several graphical interfaces/front ends for ffmpeg, it is confusing at first, but once you get a hang of what you want ffmpeg runs very easily from the command line.

[FFmpeg Basics for Beginners | Linuxers]("http://linuxers.org/tutorial/ffmpeg-basics-beginners")

---

### Post by ron999 on 2010-07-20
Hi
Like the previous poster said, ffmpeg is OK for this job.
WinFF is a 'cheap and cheerful' GUI for ffmpeg.
It has a 'Pre-set' AVI:XviD FullScreen
This produces videos with video bitrate 1500Kbps and picture size 640x480 and mp3 sound.

Using the 'Options' button allows you to tweak the settings.
So you could probably reduce the bitrate considerably.
And change the picture size to suit your camera.
And use the Additional Command Line Parameter **-an** to give no audio.

---

### Post by aust77 on 2010-07-20
Thanks to both of you, I'll try ffmpeg!

Cheers,


aust77

---

### Post by stmiller on 2010-07-20
Handbrake is awesome:

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

---

