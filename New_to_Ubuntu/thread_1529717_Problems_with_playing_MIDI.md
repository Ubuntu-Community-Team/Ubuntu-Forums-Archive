---
title: "Problems with playing MIDI"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by aprilland on 2010-07-12
Hi!
When I tried to listen to a MIDI-file, the player said that a codec is needed. The program searched codecs and suggested some "gstreamer from the bad set", 26 Mb.
Nothing changed after downloading and installing all the 26 Mb from that "bad set". Mp4 cannot be played either.](*,)
Moreover, Computer Janitor considers the packages of the "bad set" to be unnecessary and offers to delete them.
I have solved the problem with mp4 by means of installing VLC player, but I still cannot listen to MIDI.
Does any stand-alone MIDI-codec exist? I mean, a reliable one.
Thanks.

---

### Post by ajgreeny on 2010-07-12
Install **timidity** and** timidity-interfaces-extra**.  That will also suggest **freepats**, I think.  Timidity will then give you a simple GUI for playing midi files.  You might want to look at other **soundfont** packages as well, depending on how much you use midi files.

---

### Post by aprilland on 2010-07-12
Thank you, timidity does play MIDI. In a somewhat strange way, but it does. Actually, the problem is solved, though, not all tracks of midi-files are being played.

---

### Post by andrew.46 on 2010-07-13
Hi aprilland,

> **aprilland said:**
> I have solved the problem with mp4 by means of installing VLC player, but I still cannot listen to MIDI.
Does any stand-alone MIDI-codec exist? I mean, a reliable one.
Thanks.

Well actually vlc can play midi quite successfully if it has been compiled against fluidsynth. Some details here:

MIDI with VLC media player
[http://www.remlab.net/op/vlc-midi.shtml](http://www.remlab.net/op/vlc-midi.shtml)

and also the sound fonts that I use with my own setup:

Soundfonts for linux
[http://www.personalcopy.com/linuxfiles.htm](http://www.personalcopy.com/linuxfiles.htm)

Unfortunately I am not aware of any packages that are compiled in this way, it may be necessary to compile your own copy. I will be more than happy to be corrected in this assumption.

Andrew

---

