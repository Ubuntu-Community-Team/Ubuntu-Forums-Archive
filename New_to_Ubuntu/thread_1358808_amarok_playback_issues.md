---
title: "amarok playback issues"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Matt26 on 2009-12-18
i just installed amarok 2.2.2 on ubuntu 9.10 and i have a couple of issues after setting up amarok for use:

- i have no sound during playback.  my sound works fine outside of amarok (for example, system notifications) and i have tested the preferred sound output device being used via the amarok settings and they playback fine, and have even switched the preferred output device to pulseaudio (last in the list) with no success- i did get a message while i was testing them that indicated something like sound output had failed, switching to another output device (it disappeared within seconds so i can't remember exactly what this read).

- every time i try to play a different track from the previous track (in all cases the previous track hasn't finished playing yet) amarok always resumes playback of the previous track.  i found an option within the amarok settings for resuming playback when amarok starts which i disabled, but this still happens.

any help with these items would be greatly appreciated.

thanks.

---

### Post by Extract_Here on 2009-12-18
honestly switch over to Banshee as a music player it looks better and is for gnome. I had tons of trouble with amarok. with banshee no trouble.

---

### Post by Matt26 on 2009-12-18
> **Extract_Here said:**
> honestly switch over to Banshee as a music player it looks better and is for gnome. I had tons of trouble with amarok. with banshee no trouble.

thanks for the suggestion, i might give that a try, but i've used amarok in the past and i've grown to like it, and would like to continue using it.

i have faced similar issues with amarok in the past and they were resolved easily enough if i recall correctly.

---

### Post by Extract_Here on 2009-12-18
you should just give it a test drive i think you'll like it.

---

### Post by Matt26 on 2009-12-19
simple enough... for anyone else having the playback issue.

oddly enough, the second issue went away as well...

oh, and the package noted to be installed apparently doesn't exist anymore, or it was replaced... instead, install libxine1-ffmpeg.

[http://en.kioskea.net/faq/sujet-914-ubuntu-playing-mp3-files-with-amarok]("http://en.kioskea.net/faq/sujet-914-ubuntu-playing-mp3-files-with-amarok")

---

