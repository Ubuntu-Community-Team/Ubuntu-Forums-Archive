---
title: "Another no sound in game problem =S"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by Nemix on 2009-02-15
hey,
i've checked other threads on this issue and followed the advice given but im still with the issue of having not sound when i try and play a game. If i use wine and play the game's windows version the sound works fine (for certain reasons id rather not use wine, get weird screen issues.)

ubuntu is acknowledging my soundcard and it works when ever im playing music and on the Internet just when im trying to play a game i get no sound.

the games ive tried are Wolfenstein:Enemy territory and Savage2 

any help would be great =D 

few things ive tried:
-gnome alsamixer (nothing is set to mute)
-```
 sudo apt-get install alsa-oss
```

---

### Post by micoams on 2009-02-16
> 
Failed to open sound device 
/dev/dsp: Device or resource busy


I had a sound problem problem with Enemy Territory in Intrepid. The way I solved it was by disabling the Gnome sounds. Give it a try.

Go to System -> Preferences -> Sound. Click on "Sounds" tab, and uncheck "Play alerts and sound effects." Then restart the machine (or just X11 with Ctrl+Alt+Backspace).

---

