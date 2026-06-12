---
title: "How Does Record My Desktop Work?"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Seithe on 2010-02-06
How Do I work record my desktop, were does it appear? I'm guessing it should appear in Sound And Video to start it, but it doesn't so where or what do I do to start it? I opened terminal and typed in "recordmydesktop" it works there, but there's no way to stop it unless I misread on it. So how do I start it/run it and how does it work?
Though record my desktop should be closely the same as gtk record my desktop, but I don't see the stop icon that should be located on the task bar.
So can anybody help me here? Thanks.

---

### Post by Perfect Storm on 2010-02-06
You run recordmydesktop through the terminal.

```
recordmydesktop
```


more info:
```
man recordmydesktop
```

---

### Post by NCLI on 2010-02-06
If you are unfamiliar with the terminal, you can install gtk-recordMyDesktop from the Software Center. This adds a graphical interface to make it easier to use recordmydesktop.

---

### Post by Seithe on 2010-02-07
> If you are unfamiliar with the terminal, you can install gtk-recordMyDesktop from the Software Center. This adds a graphical interface to make it easier to use recordmydesktop.

Thanks.

---

### Post by quik_lives on 2010-02-07
This is great! How would I then go about converting the files to mp4 for youtube?

---

### Post by NCLI on 2010-02-07
Try installing WinFF from the Software Center, it should be able to do what you need. Also, while you're there, make sure you have the ubuntu-restricted-extras package installed. It contains a lot of video and audio codecs you may need in order to convert your file.

---

### Post by quik_lives on 2010-02-07
Much appreciated - I do have the extras installed and just installed WinFF as well. When I try to convert a 23 second test video to mp4, I get this which pops up in the terminal after I click "Convert" in WinFF:

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
  built on Oct 13 2009 22:15:16, gcc: 4.4.1
[theora @ 0x98b9d50]7 bits left in packet 82
Input #0, ogg, from '/home/carrie/out.ogv':
  Duration: 00:00:11.26, start: 0.000000, bitrate: 844 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1024x592, PAR 1:1 DAR 64:37, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 44100 Hz, stereo, s16, 499 kb/s
Unknown encoder 'libx264'
Press Enter to Continue
```

When I press Enter, it goes back to WinFF and does nothing. (Sorry to hijack this thread, but it's relevant to recording, right?

---

### Post by SlickRick on 2010-02-07
It says Unknown encoder 'libx264' so you need to download it.
Just search libx264 in synaptic and you'll find it.
If it's not there, you may need the medibuntu repository.
You can find out how to add it [here]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by CJN on 2010-02-07
Actually you probably have it but you probably auto installed FFMPEG which means the wrong flags were set, if you search there are tutorials for installing with the correct flags for proprietary work.

Actually, I'll search for you: ...

[http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg](http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg)

there, that's what you want to read.

---

### Post by quik_lives on 2010-02-07
According to Synaptic, I already have it. Two files come up - libx264-dev and libx264-67, and I marked them both for reinstallation which it says was successful, but still the same result in WinFF. For good measure I tried to install it via terminal "sudo apt-get install libx264" but it told me it couldn't find the package. Oh, and I checked, but I already have the medibuntu package.

Edit: just saw CJN's post, giving that a try.

---

### Post by quik_lives on 2010-02-07
Well evidently I've done something wrong because after all that I'm still getting the same thing. I'll tackle it tomorrow.

---

### Post by FakeOutdoorsman on 2010-02-07
> **SlickRick said:**
> It says Unknown encoder 'libx264' so you need to download it.
Just search libx264 in synaptic and you'll find it.
If it's not there, you may need the medibuntu repository.
You can find out how to add it [here]("https://help.ubuntu.com/community/Medibuntu")

Although it seems like a logical conclusion, installing a libx264 package won't enable libx264 in FFmpeg.  The **libavcodec-extra-52** package from the repository will allow FFmpeg to encode with libx264, although the version of this package from the Medibuntu repository is more versatile as it also includes libfaac for AAC audio.  More info here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **CJN said:**
> Actually you probably have it but you probably auto installed FFMPEG which means the wrong flags were set, if you search there are tutorials for installing with the correct flags for proprietary work.

Actually, I'll search for you: ...

[http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg](http://ubuntuforums.org/showthread.php?t=786095&highlight=ffmpeg)

there, that's what you want to read.

Although the above guide will provide a working (and more up to date [and my preferred method]) version of FFmpeg, the Medibuntu option I just mentioned will work too.

> **quik_lives said:**
> Well evidently I've done something wrong because after all that I'm still getting the same thing. I'll tackle it tomorrow.

Unfortunately, FFmpeg seems to have trouble decoding videos from gtk-recordmydesktop which often seem to either be corrupt or there is a bug in FFmpeg.  I believe there is a bug report already filed.  I'll look for it.

---

### Post by quik_lives on 2010-02-07
That did it! Awesome, thanks so much!

---

