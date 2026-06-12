---
title: "Audacious, Gnome ALSA Mixer, Vol. Control"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-10-20
Posted at Abs. Beg. as this is my first attempt at this.

I'm using Audacity to "record" sounds from a source. I have a cassette tape plugged into the sound card's "Line" input. I'm playing a tape (Kiri Te Kanawa). Through the various sound systems, I can hear the tape, the singing.

I'm trying to make Audacity record this. I have tried to set the Audacious/Edit/Preferences to Line (technically Line0) and have no success. The Audacity Preferences says: 

Recording

Device ALSA: SiS SI7012: SiS SI7012 - MIC ADC ( . . .

the remainder of that line scrolls off the into unreadability. I cannot pull down that menu. 

The PulseAudio Volume Control shows the the sound levels going up and down with the music. The Gnome ALSA Mixer "Line" controls the gain on the sound as well. Pulse Audio has no Server, Sink or Source set.

Please see the attached screenshots. I'm hopeful that will help your understanding.

---

### Post by Mark_in_Hollywood on 2009-10-21
After opening Audacity this morning, and looking under Edit/Preferences/Audio I/O -Record I was able to change the (seeming) default from Mic. Once I set the Recording to hardware (hw:SiS7012 etc.) and tried to record the audio from the cassette deck, it worked as expected.

**Thank you** to the 40 or so viewers of this thread.

---

