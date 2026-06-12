---
title: "Match this Xilisoft converter ultimate 6"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by mikee55 on 2011-01-23
Hi, I have Xilisofts Video Converter Ultimate 6, it does near enough everything. As well as encoding from one format to another, you can choose Video Codec,Screen Resolution,Bit Rate,Frame Rte,Zoom(Letterbox, Pan and Scan),Aspect Ratio, Audio Codec,Sample Rate, Bit Rate,Channels, Volume. Split file size, use 1 cpu core or more. You can do Apple, Zune, Wii, DS,Blackberry, DVD,VCD, mpeg3, mpeg 2, HD,SD, Xbox, PSP, PS3, Android

Its Windows and runs in Wine. Jeez, I want the same configurable package  in Linux.Handbrake, tried that, can't seem to resize resolution. Avidemux is configurable, but something seems missing. I can't match the Configuration to convert Videos for my phone extension mp4 MPEG-4 176 by 144 (qcif), Bit Rate 218 kbs, audio 44100 128kbs or my Blu Ray player's USB port that uses extension mp4 H.264 MPEG-4 AVC MPEG-4 AAC 1920 by 1080 video size, audio 48000, 5:1 Surround.

Problem is, Xilisoft keeps crashing in Wine, sometimes crashing the computer and I have to restart.

Is there any other advanced package, I can use?

Mike

---

### Post by mikee55 on 2011-01-23
Hi Update, I just tried WinFF, my needed options are plugged in, but it need a preset, I tried the obvious. But nothing. It says error.
Mike:popcorn:

---

### Post by mikee55 on 2011-01-23
Transcoder don't do it.
Mike:popcorn:

---

### Post by mikee55 on 2011-01-23
I've managed to match everything with a mp4 video that works on my phone with the settings in avidemux, but my phone refuses to play it?
Mike:popcorn:

---

### Post by mikee55 on 2011-01-23
I'm all alone!

---

### Post by BugBuster on 2011-01-23
Install ffmpeg and try this;
```
 ffmpeg -i <input_file> -vcodec mpeg4 -vb 218k -s 176x144 -acodec libmp3lame -ab 128k -ar 44100 output.mp4
```
Then try playing the output video on your phone and post the results..

---

### Post by mikee55 on 2011-01-23
ffmpeg -i <input_file> -vcodec mpeg4 -vb 218k -s 176x144 -acodec libmp3lame -ab 128k -ar 44100 output.mp4

Sorry, need help with command line.

---

### Post by mikee55 on 2011-01-23
The file is called coyote3d and is in my video folder, in my home folder.

---

### Post by BugBuster on 2011-01-23
Hi mikee55,

Just replace <input_file> with the actual name of the video file you wish to convert and output.mp4 with the name you want for your output file. Copy/paste the other command line as it is after installing ffmpeg!

---

### Post by Elfy on 2011-01-23
> **mikee55 said:**
> I'm all alone!

First - please do not bump your thread as often as you did.

Second - if you are going to add information after you've posted it is better in my opinion to edit the first one - people search for unanswered threads as soon as you start bumping that's gone.

---

### Post by mikee55 on 2011-01-23
Ubuntu forums staff.

I only bumped once. The other posts were updates.

Thanks:D

---

### Post by Elfy on 2011-01-23
> **mikee55 said:**
> Ubuntu forums staff.

I only bumped once. The other posts were updates.

Thanks:D

They are all in effect bumps ;)

---

### Post by mikee55 on 2011-01-23
Okay they were bumps, it wasn't intentional. Sorry:confused::oops:


In a Terminal
System-Product-Name:~$ ffmpeg -i<coyote3d> -vcodec mpeg4 -vb 218k -s 176x144 -acodec libmp3lame -ab 128k -ar 44100 coyote3d.mp4
bash: coyote3d: No such file or directory


Is this no good?

Mike
[IMG]http://img12.imageshack.us/img12/7937/screenshot2vh.png[/IMG]
By [mikeezpic](http://profile.imageshack.us/user/mikeezpic) at 2011-01-23

---

### Post by Elfy on 2011-01-23
I think it needs to be 

```
ffmpeg -i coyote3d -vcodec mpeg4 -vb 218k -s 176x144 -acodec libmp3lame -ab 128k -ar 44100 coyote3d.mp4
```

at least that's how it looks to me.

Though does the input file have no extension?

---

### Post by BugBuster on 2011-01-23
Try this..
```
ffmpeg -i Videos/coyote3d -vcodec mpeg4 -vb 218k -s 176x144 -acodec libmp3lame -ab 128k -ar 44100 coyote3d.mp4
```

---

### Post by mikee55 on 2011-01-23
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'Videos/coyote3d':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: mp41
    encoder         : Lavf51.12.1
  Duration: 00:02:59.00, start: 0.000000, bitrate: 279 kb/s
    Stream #0.0(und): Video: mpeg4, yuv420p, 176x144 [PAR 72:59 DAR 88:59], 163 kb/s, PAR 107:88 DAR 107:72, 15 fps, 15 tbr, 15 tbn, 15 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 112 kb/s
Output #0, mp4, to 'coyote3d.mp4':
  Metadata:
    encoder         : Lavf52.64.2
    Stream #0.0(und): Video: mpeg4, yuv420p, 176x144 [PAR 107:88 DAR 107:72], q=2-31, 218 kb/s, 15 tbn, 15 tbc
    Stream #0.1(und): Audio: libmp3lame, 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame= 2685 fps=398 q=2.0 Lsize=    7452kB time=178.78 bitrate= 341.4kbits/s    
video:4582kB audio:2793kB global headers:0kB muxing overhead 1.037259%

Phone says "Not supported content"
[[IMG]http://img41.imageshack.us/img41/3786/screenshotvhu.png[/IMG]](http://img41.imageshack.us/i/screenshotvhu.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
The only difference is audio codec.
[[IMG]http://img268.imageshack.us/img268/3929/coyotes.png[/IMG]](http://img268.imageshack.us/i/coyotes.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Uploaded with [ImageShack.us](http://imageshack.us)
Mike

---

### Post by TiberiusT on 2011-01-23
There's tonnes of stuff around for FFmpeg and it's really the only way to go for proper transcoding. You'll get much better quality once yu learn the command line options and you'll be in full control of the output which yu never really are using a GUI.

from my bookmarks:

[http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/)
[http://howto-pages.org/ffmpeg/](http://howto-pages.org/ffmpeg/)
[http://ffmpeg.arrozcru.org/](http://ffmpeg.arrozcru.org/)
[http://rodrigopolo.com/ffmpeg/cheats.html](http://rodrigopolo.com/ffmpeg/cheats.html)
[http://www.ffmpeg.org/ffmpeg-doc.html](http://www.ffmpeg.org/ffmpeg-doc.html)

It's def worth the time investment!

T

---

### Post by mikee55 on 2011-01-23
Cheers T, I'm off to learn.
Thanks to Bugbuster and Forest Piskie

Mike:P

---

