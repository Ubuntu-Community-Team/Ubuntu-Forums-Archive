---
title: "Rosegarden MIDI No Sound"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by darkfeline on 2010-01-02
Quite simply, when I try to play a file, Rosegarden shows it as playing, but there's no sound.

I know that you need a MIDI synthesizer; I start timidity as a daemon in a terminal with 'timidity -iA -B2,8 -Os1l -s 44100' and I go to MIDI devices and make sure that they point to the opened MIDI ports (And yes, I make sure volume is unmuted), but there's still no sound.  It's weird because I got it working before, but now it refuses to output sound.  Help please!

---

### Post by stoogiebuncho on 2010-01-07
I haven't used Rosegarden, but I found in some other music software, you have to specify in the settings where your sound device is.  Generally it's at hw:0

So look through the settings and see if there's a box to specify the sound device, and put hw:0 in there and try it again.

---

