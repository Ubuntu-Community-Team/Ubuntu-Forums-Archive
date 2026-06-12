---
title: "last.fm couldnt start playback through rhythmbox plugin."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by cirrusminora on 2009-02-08
I've been trying to play last.fm from the rhythmbox plugin.I have provided my account specifics and it shows my status as Ok. However,I get this error message on searching and clicking a "similar artist radio" : Couldn't start playback.Could not open resource for reading.

Can rhythmbox play only those streams which I've tagged in my last.fm profile ? Or indeed I can search anything from rhythmbox and expect it to work ? Thanks in advance.Do help.

---

### Post by cirrusminora on 2009-02-15
No one about,people ?I need to get this working badly.

---

### Post by MasterProg on 2009-02-15
What version of Rhythmbox are you using?

---

### Post by teknostatik on 2009-02-15
> **cirrusminora said:**
> 

Can rhythmbox play only those streams which I've tagged in my last.fm profile ? Or indeed I can search anything from rhythmbox and expect it to work ? Thanks in advance.Do help.

You should be able to search for anything from within Rhythmbox and expect it to work. I've just tried this with Rhythmbox 0.11.6 running on Ubuntu 8.10 and it works as expected.

What version of Ubuntu/Rhythmbox are you using?

Regards,

Andy

---

### Post by MasterProg on 2009-02-15
* I suspect the problem is because of an old version of Rhythmbox. The version shipped with Ubuntu 8.10 uses a new streaming engine. It is possible that something on last.fm has changed lately and the old version doesn't work any more.

---

### Post by cirrusminora on 2009-02-16
I'm using Rhythmbox 0.11.2 on gutsy 7.10. I've tried adding the repository for the latest 0.11.6 but on update,terminal gets stuck at (99 % finished,waiting for headers)  However Last.fm gets the library updates of song I've been playing in rhythmbox.But not vice versa,i.e- not being able to play anything from the website.

Can I make it work with the current version?If not,is there a repository from where I  can download the 0.11.6 ?

---

### Post by cirrusminora on 2009-02-16
I had forgotten to instruct the website to play only through external player.I did that,but I get a new error,which is apparently a known bug. Error message reads "Problem occurred without error being set. This is a bug in Rhythmbox or GStreamer." I opened rhythmbox and checked the logs.On requesting Last.fm to play a "Segovia Radio", I get the following log :

 (21:22:46) [0x80fb408] [rb_lastfm_perform] rb-lastfm-source.c:737: Last.fm communicating with [http://ws.audioscrobbler.com/radio/adjust.php?session=a0e76c17ecf4f0561d92de7451816f57&url=http://www.last.fm/listen/artist/segovia/similarartists&debug=0](http://ws.audioscrobbler.com/radio/adjust.php?session=a0e76c17ecf4f0561d92de7451816f57&url=http://www.last.fm/listen/artist/segovia/similarartists&debug=0)
(21:22:47) [0x80fb408] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:817: Not doing handshake; we already have one
(21:23:02) [0x80fb408] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:817: Not doing handshake; we already have one
(21:23:17) [0x80fb408] [rb_audioscrobbler_should_handshake] rb-audioscrobbler.c:817: Not doing handshake; we already have one

I'm a complete noob and though the plugin initaialises and "hand-shakes" in the start,on requesting a stream,it just goes bump,refusing to shake hands twice ! I have browsed for this error message but can't find anything conclusive,short of uninstalling my current version and installing latest (don't have the repos for that).

Hope someone chips in.

---

### Post by MasterProg on 2009-02-17
Well, I can't really get what is causing the problem, but if you just want to listen to the radio you can use the official client or Last Exit.
```
sudo apt-get install lastfm
sudo apt-get install last-exit
```

---

