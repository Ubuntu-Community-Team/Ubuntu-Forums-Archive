---
title: "Every video player doesn't work."
date: 2010-03-17
forum: New to Ubuntu
---

### Post by JerichoKru on 2010-03-17
I've installed mplayer, gnome-mplayer, xine, gxine, vlc, and smplayer and none of them work.

gnome-mplayer -v
```
jericho@JerichoXubuntuNote [ ~ ] % gnome-mplayer -v
GNOME MPlayer v0.9.8
vo = (null) ao = (null)
Running with GIO support
Front,0 Playback is 1
Front,0 Range is 0 to 42 
Front,0 Current Volume 3, multiplier = 2.380952
Scaled Volume is 7.142857
Using volume of 7.00
Using softvol, setting volume to max (will be limited by mixer 100% of 7%)
Using match: type='signal',interface='com.gnome.mplayer'
Using match: type='signal',interface='org.gnome.SettingsDaemon'
Using match: type='signal',interface='org.gnome.SettingsDaemon.MediaKeys'
Proxy connections and Command connected
opening playlist
playlist detection = 0
adding file:///home/jericho/Videos/Muse%20-%20Resistance%20(Ti%C3%ABsto%20Remix).mp4 to playlist (cancel = 0)
playing - file:///home/jericho/Videos/Muse%20-%20Resistance%20(Ti%C3%ABsto%20Remix).mp4
is playlist 0
getting file metadata for /home/jericho/Videos/Muse - Resistance (Tiësto Remix).mp4
file:///home/jericho/Videos/Muse%20-%20Resistance%20(Ti%C3%ABsto%20Remix).mp4 is not marked as playable (1)

```
After this, gnome-mplayer actually freezes

mplayer
```
jericho@JerichoXubuntuNote [ ~ ] % mplayer
mplayer: symbol lookup error: mplayer: undefined symbol: codec_wav_tags

```

I removed the others...because I was trying different things (and xine, gxine, smplayer, and vlc were ugly and did not fit into my theme at all)

---

### Post by fatality_uk on 2010-03-17
Were you going to ask a question? There are oft

---

### Post by wjm on 2010-03-17
to solve the mplayer bug just remove package  libavutil50 - that seems to be causing it - it's a third party issue.

---

### Post by JerichoKru on 2010-03-18
> **wjm said:**
> to solve the mplayer bug just remove package  libavutil50 - that seems to be causing it - it's a third party issue.

Doing so also removes these packages:

```
gnome-mplayer
libavcodec52
libavformat52
libpostproc51
libswscale0
mplayer
mplayer-nogui

```

First one I actually need.  How do I remove just the one thing?

---

### Post by JerichoKru on 2010-03-18
Respectful bump, since I find this somewhat serious.

---

### Post by sandyd on 2010-03-18
seems like theirs a difference between the version of ffmpeg, and the version of ffmpeg that mplayer/vlc was compiled against.

Tell me. Have you added any repositories?

and try```

sudo apt-get install ffmpeg libavcodec-unstripped-52 libavdevice-unstripped-52 libavfilter-unstripped-0 libavformat-extra-52 libpostproc-extra-51 libswscale-extra-0 libavutil-extra-49
```

---

### Post by JerichoKru on 2010-03-18
> **carlee said:**
> seems like theirs a difference between the version of ffmpeg, and the version of ffmpeg that mplayer/vlc was compiled against.

Tell me. Have you added any repositories?

and try```

sudo apt-get install ffmpeg libavcodec-unstripped-52 libavdevice-unstripped-52 libavfilter-unstripped-0 libavformat-extra-52 libpostproc-extra-51 libswscale-extra-0 libavutil-extra-49
```

I have quite a few extra repos, mostly ones that are in UbuntuTweak that can be added.  I can post my sources.list if you need it.


The command:

```
jericho@JerichoXubuntuNote [ ~ ] % sudo apt-get install ffmpeg libavcodec-unstripped-52 libavdevice-unstripped-52 libavfilter-unstripped-0 libavformat-extra-52 libpostproc-extra-51 libswscale-extra-0 libavutil-extra-49
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ffmpeg: Depends: libavcodec52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavdevice52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavfilter0 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libavformat52 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libpostproc51 (>= 5:0.5+svn20091116) but it is not going to be installed
          Depends: libswscale0 (>= 5:0.5+svn20091116) but it is not going to be installed
E: Broken packages

```

---

### Post by JerichoKru on 2010-03-19
No none has a solution?

---

### Post by JerichoKru on 2010-03-21
nothing?

---

### Post by JerichoKru on 2010-03-22
I guess I'll just have to resort to a re-install of xubuntu.

---

### Post by arochester on 2010-03-22
You might look at "Comprehensive Multimedia & Video Howto" - [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by JerichoKru on 2010-03-23
> **arochester said:**
> You might look at "Comprehensive Multimedia & Video Howto" - [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Not helpful, but thanks anyway.

---

### Post by JerichoKru on 2010-03-24
Doesn't anyone have a solution/workaround?

---

