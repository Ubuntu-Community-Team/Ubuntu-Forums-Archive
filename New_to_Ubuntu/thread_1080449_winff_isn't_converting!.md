---
title: "winff isn't converting!"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-02-25
I am having trouble using winff. I was able to install but when I run it and try to convert, it doesn't work.

I first tried to convert .flv to .mp3 and thought maybe I can't convert from video to audio (which I don't see why not!) and then tried to convert .flv to .mp4 and it still didn't work.

When I converted from .flv to .mp3, the file gets created but it's empty. Here's the output (the first two lines are outputted about a million times on the console):
```
[flv @ 0xb7f83388]Unsupported video codec (7)
[flv @ 0xb7f83388]Unsupported video codec (7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/home/sylvainrb/Videos/hitohira no hanabira.flv':
  Duration: 00:03:35.7, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: 0x0007, 25.00 tb(r)
    Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Output #0, mp2, to '/home/sylvainrb/Documents/converted media/hitohira no hanabira.mp3':
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, 160 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec (id=0) for input stream #0.1
Press Enter to Continue

```

I have also installed the unstripped packages...

---

### Post by sylvainrb on 2009-02-25
Ok so winff is working! Apparently it is a problem with the file: from the output on the previous post, it has to do with the frame rate.

Does anyone has any idea how to fix it? Or find a way to change the frame rates?

Thanks!

---

### Post by mangurt on 2009-02-25
You should be able to change the frame rate in the advance options with winff.

---

### Post by opscure on 2009-02-25
You can try mencoder:
```
mencoder testflv.flv -oac copy -ovc frameno -o outputtest.mp3
```

---

### Post by sylvainrb on 2009-02-25
No mencoder isn't working either.

As for changing frame/bit rates in winff in the options, I don't know what to put in or change it too.

Actually, I think the problem is in some of the videos. They are youtube videos but some work and others don't. The ones I can't convert don't work in amarok, vlc but do in totem. Any ideas why?

---

### Post by opscure on 2009-02-25
First what error is mencoder reporting?  Do you have all the codecs installed?

The reason you are likely seeing some that work and others that don't is because youtube allows uploading of various formats and converts it to the flv file through whatever video codec the initial file was in.  You likely don't have the proper codecs installed for your applications.

---

### Post by sylvainrb on 2009-02-25
I already uninstalled mencoder since I found out that winff was working fine, but the error message was similar as that the codec was unsupported.

As for all the available codecs, what are they and are they listed in synaptic?

---

### Post by opscure on 2009-02-26
I don't use winff, but here is the wiki page for installation. 
[http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)

Here's the list of the working codecs for mplayer/mencoder:
[http://www.mplayerhq.hu/DOCS/codecs-status.html]("http://www.mplayerhq.hu/DOCS/codecs-status.html")

Proprietary/restricted codecs (any windows based ones) cannot be included in synaptic by default because of legal issues.  That's not to say, if you can find a repository that houses them, that you cannot just add them yourself to your apt sources. You may want to enable the restricted sources as well.

Good luck.

---

