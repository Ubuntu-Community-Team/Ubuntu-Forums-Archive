---
title: "banshee starts on its own"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by werty2010 on 2011-07-29
i use banshee as my main media player and from time to time while it's playing i pause it.
there are sometimes when it's playing the music on it's own(!), without me pressing any key...
some help to figure this out?

---

### Post by androssofer on 2011-07-29
> **werty2010 said:**
> i use banshee as my main media player and from time to time while it's playing i pause it.
there are sometimes when it's playing the music on it's own(!), without me pressing any key...
some help to figure this out?

do u mean it randomly unpauses itself and starts playing? 

or tht its closed and randomly starts up, then plays?

---

### Post by werty2010 on 2011-07-29
> **androssofer said:**
> do u mean it randomly unpauses itself and starts playing? 

or tht its closed and randomly starts up, then plays?

the first one

---

### Post by ajgreeny on 2011-07-29
The keyboard shortcut for play is space-bar, so I wonder if you just happen to hit that while the music player is active.  Do you have your mouse settings to bring windows to the front when you mouse-over them, rather than click in the window?

---

### Post by werty2010 on 2011-07-29
> **ajgreeny said:**
> The keyboard shortcut for play is space-bar, so I wonder if you just happen to hit that while the music player is active.  Do you have your mouse settings to bring windows to the front when you mouse-over them, rather than click in the window?

i don't think this it because about 90% of time banshee runs on the background and when i want to stop/pause it i reopen it from the system tray and click the button

---

### Post by Vondis on 2011-09-16
I have this issue as well. I am running ubuntu 10.04 64bit. Banshee is paused and will randomly start playing all by itself. No it is not my keyboard nor is it my mouse. I know this because everytime it has happened I wasn't on the computer. I was either on the couch watching tv or in the next room and music starts playing out of nowhere and I am like wtf is going on. Walk in the room go to puter and banshee is playing the song it was paused on. Any ideas on this would be much appreciated.

---

### Post by kakaw on 2011-12-19
I've been having this problem as well, also since July. I'm running version 2.0.1 on Ubuntu 10.04 (Lucid). I was about to file a bug report at Bugzilla, when I read the part that said "Reproduce your bug using a recent build of the   software, to see whether it has already been fixed."  The most recent version out is 2.2. I'm gonna try upgrading and see if the Random Unpause bug goes away.

---

### Post by kakaw on 2011-12-19
Turns out Banshee 2.2 is not available for Lucid. (More info here: [http://osdir.com/ml/banshee-list/2011-10/msg00166.html](http://osdir.com/ml/banshee-list/2011-10/msg00166.html))

I've filed a bug report here: [https://bugzilla.gnome.org/show_bug.cgi?id=666564](https://bugzilla.gnome.org/show_bug.cgi?id=666564)
If you're having this problem, please add any info you may have to the report.

---

### Post by kakaw on 2012-01-10
This problem seems to be linked to Banshee's Alarm Clock extension.  When I "turned off" the extension, Banshee stopped spontaneously initiating playback.

Edit > Preferences > Extensions > Community Extensions > untick the "Alarm Clock" box.

---

