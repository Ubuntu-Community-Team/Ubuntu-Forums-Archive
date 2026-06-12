---
title: "Disable Guifications (pidgin) during full screen video playback"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-03-17
I'm watching a movie using smplayer or vlc in full-screen and pidgin notifications keep popping up. This is really distracting (and the sound is also annoying). Is there anyway to disable this when Smplayer or VLC goes full-screen?

(NB: I don't want to turn of pidgin during these times, just disable guifications temporarily).

Thanks!

---

### Post by D3ath on 2009-03-17
> **abhiroopb said:**
> I'm watching a movie using smplayer or vlc in full-screen and pidgin notifications keep popping up. This is really distracting (and the sound is also annoying). Is there anyway to disable this when Smplayer or VLC goes full-screen?

(NB: I don't want to turn of pidgin during these times, just disable guifications temporarily).

Thanks!

Yea go to pidgin select Tools > Plugins > Check off the guifications plugin to off.

---

### Post by abhiroopb on 2009-03-17
> **D3ath said:**
> Yea go to pidgin select Tools > Plugins > Check off the guifications plugin to off.

Yes I know about that, but is there a way to automate it?

---

### Post by iamkrazee on 2009-03-17
Just stay away.. I mean the status.

---

### Post by abhiroopb on 2009-03-17
> **iamkrazee said:**
> Just stay away.. I mean the status.

Its set to away (always)

---

### Post by LowSky on 2009-03-17
the GUIfication plugin has options to only work when you are availible. So if you select away it will turn notifications off., you other option is to turn the sound off of people loggin in and out(which I do becasue I cant stand it).

Pidgin wasn't built with fullscreen movies in mind, so you need to play to that, sorry 'tis life. then again neither is AIM, mine annoys the crap out of me in Windows when playing Games or Movies, if I forget to shutdown AIM (the door closing noise has made me jump a few times during some intense movies... never see it coming...lol).

---

### Post by sdennie on 2009-03-17
Pidgin doesn't use standard gconf stuff so this might be hard.  If you are using compiz, you could probably find a way to write a rule to make guifications always appear below the media player windows.  You could also see if pidgin talks to dbus or write a sed command in a media player wrapper to comment out/uncomment the loading the guification plugin in ~/.purple/prefs.xml but, I don't know if pidgin reacts in realtime to external XML changes.

---

### Post by iamkrazee on 2009-03-18
Pidgin does listen to DBus through a plugin.

---

