---
title: "need converter from .ogg or .wav to .amr"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by spearfish on 2010-08-18
Can anyone recommend a sound converter that can take a .ogg or a .wav file and convert it to .amr?

We are programming for a Nokia phone and we need to record some .amr files.  I've got my microphone working, but the recording software only saves in ogg and wav.

cheers!

---

### Post by grobar87 on 2010-08-18
sorry wrong link...

---

### Post by fbobraga on 2010-08-18
This may do it: a GUI frontend to ffmpeg - [http://winff.org/](http://winff.org/)

It's in the repos:
```
sudo apt-get install winff
```

---

### Post by spearfish on 2010-08-18
Oh, I answered my own question.  There is a good program called: Mobile Media Converter from Miksoft.  They have a Ubuntu/DEB package.

---

### Post by andrew.46 on 2010-08-18
Hi Spearfish,

If you wanted to use FFmpeg *directly* have a look at this guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and then you can easily convert your files with syntax similar to the following:

```
ffmpeg -i input.wav -acodec libopencore_amrnb \
        -ac 1 -ar 8000 -r 25 -ab 12200 output.3gp
```

I double checked this with a test file and it ran nicely:

```

andrew@skamandros~/Desktop$ [B][COLOR="Red"]ffmpeg -i input.wav -acodec libopencore_amrnb \
>         -ac 1 -ar 8000 -r 25 -ab 12200 output.3gp[/COLOR][/B]
FFmpeg version SVN-r24802, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug 17 2010 21:16:31 with gcc 4.4.4
  configuration: --prefix=/usr --mandir=/usr/man --enable-postproc 
--enable-avfilter --enable-pthreads --enable-shared --disable-static 
--disable-ffserver --enable-libtheora --enable-libvorbis --enable-x11grab 
--enable-libmp3lame --enable-libx264 --enable-libfaac 
--enable-libopencore-amrnb --enable-libopencore-amrwb --enable-version3 
--enable-zlib --enable-libvpx --enable-libgsm --enable-nonfree 
--enable-gpl
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 4. 0 /  0. 4. 0
  libavcodec    52.85. 1 / 52.85. 1
  libavformat   52.78. 3 / 52.78. 3
  libavdevice   52. 2. 1 / 52. 2. 1
  libavfilter    1.34. 1 /  1.34. 1
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[wav @ 0x807b470] max_analyze_duration reached
[wav @ 0x807b470] Estimating duration from bitrate, this may be inaccurate
Input #0, wav, from 'input.wav':
  Duration: 00:06:05.24, bitrate: 1411 kb/s
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Output #0, 3gp, to 'output.3gp':
  Metadata:
    encoder         : Lavf52.78.3
    Stream #0.0: Audio: libopencore_amrnb, 8000 Hz, 1 channels, s16, 12 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
size=     643kB time=365.26 bitrate=  14.4kbits/s    
video:0kB audio:571kB global headers:0kB muxing overhead 12.597533%

```

Andrew

---

### Post by xMP44x on 2010-08-18
From what I remember Audacity can perform the function you are looking for. It's available on Windows, and in Ubuntu's Software Center. Open the .ogg file and then choose to export it as a .wav. I know it worked for me on Windows, but I only recently tried out Ubuntu so I'm still learning,

---

