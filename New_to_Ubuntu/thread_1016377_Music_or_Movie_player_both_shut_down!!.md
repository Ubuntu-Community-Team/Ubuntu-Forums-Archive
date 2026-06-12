---
title: "Music or Movie player: both shut down!!"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-19
Ok, I`m not being very patient maybe. But first I spent weeks after installing Hardy Heron (and I`m a noob :) ) before I could hear any videos or movies. Then after about a week of asking and doing (on this forum) it was great to have the problem fixed. Then suddenly after getting updates for Ubuntu, I can`t do ANYTHING aaaaaahhhhhhhh!  Anytime I try to play anything, the player (movie, mp3 whatever) just shuts down, whether a file in my computer, or on a youtube site. I have already asked and done, again, but I`m not getting anywhere. I`m usually more patient, as I understand there are so many people like me...I just can`t understand how everything was `fixed` then suddenly..I hope someone can help me fix this. Only thing I want for Christmas lol.

---

### Post by taurus on 2008-12-19
Try to run it from a terminal to see what the error message is.

Applications -> Accessories -> Terminal
```
vlc movie_file.avi
```
Which media player do you use?

---

### Post by Lakeside5 on 2008-12-19
Here is what I get, and thanks for showing how to play it in the terminal too.:

VLC media player 0.8.6e Janus
[00000345] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[00000346] pulse audio output error: Failed to connect to server: Invalid argument
[00000346] pulse audio output error: Pulse initialization failed
*** PULSEAUDIO: Unable to create stream.
*** PULSEAUDIO: Unable to create stream.
[00000346] alsa audio output error: unable to commit hardware configuration (Input/output error)
vlc: pcm_pulse.c:115: pulse_stop: Assertion `pcm->stream' failed.
Aborted
I try to use vlc, or movieplayer, I have both in here. For mp3`s I tried rhythmbox. thanks

---

### Post by Lakeside5 on 2008-12-20
So..what do I do now?  Anybody?:confused:
So maybe Ihave to start all over, re-install Hardy? maybe even the 8.10 version, but I read it has a lot of bugs :(.  I have followed all kinds of suggestions here, googled all kinds of help too, everything from the restricted extras to other fixes, yet the players keep closing! It`s all I want for Christmas, really, a linux distro that works with sound and everything lol.

---

