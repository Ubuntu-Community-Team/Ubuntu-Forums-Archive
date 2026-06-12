---
title: "sound problem with wine"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2009-02-01
Hi All,
I just downloaded TefView 2.65, a guitar tablature reader and can run it through wine. Now everything works with it except the sound. I have followed a few threads and checked the wine config and all the sound tests work. Does that tell me anything? Another thread held out little hope getting the midi out working in wine on some other software. I should say that the sound on my computer works fine in every other application so I assume it must be wine that is the problem. Can anyone tell me where to start looking to fix this or is there a guitar tab reader that runs on Linux?
Cheers

---

### Post by llamabr on 2009-02-01
Wine sucks.  It's always the last alternative, not a starting place.  For some reason, new users keep being drawn to it, but in my experience, it rarely works, and it's rarely required.  If you need to run .exe files all over the place, you're using the wrong OS.

In answer to your final question -- sure, there's plenty you can do in linux:

brock@vader:~$ apt-cache search guitar
abcmidi - converter from ABC to MIDI format and back
cheesetracker - sound module tracking program (IT - Impulse Tracker clone)
creox - real-time guitar effects
etktab - ASCII guitar tab editor
exaile - flexible audio player, similar to Amarok, but written in GTK+
fretsonfire - game of musical skill and fast fingers
fretsonfire-game - game of musical skill and fast fingers - Game files
fretsonfire-songs-sectoid - game of musical skill and fast fingers - Songs Package
gnometab - WYSIWYG GNOME2 Program for creating guitar tabs
gtkguitune - Guitar and other instruments tuner
kguitar - Stringed instrument tablature editor for KDE
lilypond - A program for typesetting sheet music
line6-usb-source - Line 6 POD driver source
lingot - accurate and easy to use musical instrument tuner
songwrite - guitar tablature editor and player
texlive-music - TeX Live: Music typesetting
tuxguitar - Multitrack guitar tablature editor and player (gp3 to gp5)
tuxguitar-alsa - tuxguitar plugin for sound playback using ALSA
tuxguitar-fluidsynth - tuxguitar plugin for sound playback using fluidsynth
tuxguitar-jsa - tuxguitar plugin for sound playback using Java Sound API
tuxguitar-oss - tuxguitar plugin for sound playback using OSS
brock@vader:~$

---

### Post by Dermot Doyle on 2009-02-02
Thanks, I'll start working my way through your list.

---

### Post by thomas_toscani on 2010-05-31
> **Dermot Doyle said:**
> Hi All,
I just downloaded TefView 2.65, a guitar tablature reader and can run it through wine. Now everything works with it except the sound. I have followed a few threads and checked the wine config and all the sound tests work. Does that tell me anything? Another thread held out little hope getting the midi out working in wine on some other software. I should say that the sound on my computer works fine in every other application so I assume it must be wine that is the problem. Can anyone tell me where to start looking to fix this or is there a guitar tab reader that runs on Linux?
Cheers

I had the same problem with no sound in TefView under Wine.  I am running Ubuntu 10.04.

I have found a solution - two solutions in fact.

**Solution 1:**

Download, install, and start Timidity: 

[http://timidity.sourceforge.net/#info](http://timidity.sourceforge.net/#info)

>sudo apt-get install timidity should do it.  

You then need to start timidity with:

>[FONT=Verdana, Arial, Helvetica]timidity -iA -Os

You then need to configure your MIDI Setup in TefView using the menu.

**Solution 2:**

Download and install Tuxguitar:

[http://tuxguitar.herac.com.ar/](http://tuxguitar.herac.com.ar/)

You'll then need to Import each Tef file in order to view and play it.

---
Thanks Kingfisher for the original post:

[http://www.banjohangout.org/topic/169479](http://www.banjohangout.org/topic/169479)


[/FONT]

---

