---
title: "Audio Equalizer For Linux?"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by Tman5293 on 2009-09-26
Hi,

I was wondering if there is an audio equalizer for Linux. You see I really like to get the best sound quality possible out of my music and speakers and I would really like to be able to control what the audio coming from my speakers sounds like. To do this I need an equalizer so I just wanted to know if one exists for Linux?

Thanks!

---

### Post by niteshifter on 2009-09-26
Hi,

Yes .... and no. The sound sub-system (Pulseaudio) provides for system-wide EQ, but there are some caveats. See [this page]("http://ubuntuforums.org/showthread.php?t=789578") (ubuntuforums.org), toward the bottom (Appendix "D").

Various player applications have their own EQ. Myself, I use Audacious for music playback (has an EQ, with preset capability). For movies I use VLC (also has an EQ). There are other apps that feature EQ. 

FWIW I tried the Pulseaudio system-wide EQ on Hardy (8.04.2) - it works but there's a hassle factor - there seems to be no GUI for the EQ function, I had to edit the file ~/.asoundrc to make setting changes, plus logout and back in. As I have different headphones / speakers that I use I found the current implementation of EQ via Pulseaudio lacking.

---

