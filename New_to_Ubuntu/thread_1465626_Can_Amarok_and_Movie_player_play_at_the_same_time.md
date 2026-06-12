---
title: "Can Amarok and Movie player play at the same time ?"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by davexnet on 2010-04-29
Hello,
I had Amarok open listening to some tunes, and I remembered
there was some video I wanted to check.  Opened up
"movie player", but the file refused to play,
it just sat there at the start.

Once I closed Amarok, the video started to play.

I uninstalled "movie player" and installed the "Gnome Mplayer",
but it behaved exactly the same .

I've never heard of the restriction before.  Is it "normal behavior" or
is there something amiss ?

Thanks for any info .
PS it's occurring with Amarok 2.3 in Ubunto 9.10

---

### Post by agnes on 2010-04-29
Check for Amarok and Mplayer/Movie Player, the audio output method they use... (in the settings of those applications it must be somewhere, it is 'ALSA' or 'OSS' or 'PulseAudio'). afaik Alsa's OSS emulation can hijack the soundcard. Check if it works if you set both Amarok and Mplayer/Movie Player to use 'ALSA'.

---

### Post by davexnet on 2010-04-29
Thanks for this info.  I set Mplayer to use "Pulse",
the other audio options being alsa, arts, erd, jack & oss.

In the Amarok choices were Intel ICH with ALC655 amd Pulse Audio,
I assume it's using ALC655, since it's first in the list.

Anyway, with them set this way, they play simultaneously .

Appreciate it -
Dave

---

### Post by davexnet on 2010-04-30
I should add that although it's working, it's not optimal.
They're are some crackles and occasional small beak-ups or
hesitations in the audio -
Even the jingle when Ubuntu first starts up sometimes glitches.

Never seen that before.  Perhaps there's a confict somewhere ?

---

