---
title: "MPD &amp; Ubuntu-Server"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by arrrghhh on 2010-04-23
I posted this over in the server section, without much luck.  Essentially I run MPD on my server, so no pulse.  Previously I was using pulse to play music with MPD, but it was a pain to get pulse to run sessionless - I don't want to have a user logged into my server to have functional audio/music :D

So I'm trying to stick with alsa this time (unless someone has a good suggestion for my pulse-as-a-service issue) and every time I try to play a song in MPD it crashes.  It is a fresh server install, so I thought at first codecs.  I didn't install ubuntu-restricted-extras, I just want audio-related codecs.  So I believe I have all of those installed correctly, still MPD crashes.

So I turned to alsa.  Had to install alsa-utils to get alsamixer to work.  The volume was all turned down, and MPD was showing volume as N/A until I cranked it up in alsamixer.  Now MPD shows 100% for volume, progress!  But it still crashes as soon as I try to play a song.

It found/updated my entire library without any fuss really, and I can play songs with mplayer (needed for PS3MediaServer...) - so I know I at least have some codecs right... perhaps not the correct ones for MPD?

So any advice would be much appreciated.  I love MPD, simply the best CLI music player there is.  I can control it from any PC anywhere in the world, and MusicPlayerMinion for Firefox is better than most full-featured music clients IMHO!!  I miss my MPD!!

---

### Post by arrrghhh on 2010-04-23
Anybody use MPD?  I should try it on a -desktop liveCD to see if there's a difference... I really like the stripped server install, I don't need much, but I think the problem is I don't know what MPD needs to play...

---

### Post by arrrghhh on 2010-04-23
Found a segfault...

```
[161048.253573] mpd[22957] general protection ip:b6efc1b5 sp:b53e1850 error:0 in libavcodec.so.52.20.1[b6ab4000+52b000]
```

Looks codec related :P  Just not sure what codec, I'm pretty sure I have all the right codecs installed.

MPD spit this out:
```
decoder: audio_format=44100:16:2, seekable=true
Segmentation fault
```

Any help?

Update - see [this](http://ubuntuforums.org/showthread.php?t=1460338) for solution.  Or a one-sided conversation.

---

