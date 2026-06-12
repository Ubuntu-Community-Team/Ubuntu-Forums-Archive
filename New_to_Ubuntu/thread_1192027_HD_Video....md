---
title: "HD Video..."
date: 2009-06-19
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-06-19
As you can see from my PC specs in my signature below I shouldn't have the slightest problem with playing 1080p video but for some reason I do...but only with what I assume are intense cpu usage areas of a film? for instance the opening for the first episode of the program Planet Earth in x264 1080p mkv file where you see all the birds (it gradually pans out until the screen is full of thousands of cranes?) I get very very jerky playback until eventually it will stop playing the video and skip ahead

I have tried compiling mplayer with Multi core support but it doesn't seem to be making a difference;)

I'm running jaunty x64

---

### Post by shifty_powers on 2009-06-19
have you tried vlc?

---

### Post by TheBuzzSaw on 2009-06-19
I am not familiar with mkv files, but I wanted to ask: are you reading it straight from the disc? Or are you reading from a file you have saved onto your hard drive?

(I love Planet Earth. I think I'll go watch it again. ^_^)

---

### Post by fooman on 2009-06-19
have a look at this very nice guide:

[http://ubuntuforums.org/showthread.php?t=1037625](http://ubuntuforums.org/showthread.php?t=1037625)

hope it helps you....it did for me (running jaunty 64 w/nvidia 8800gt)!  :D

---

### Post by H2SO_four on 2009-06-19
Vlc player works well with my setup.

---

### Post by kamitsukai on 2009-06-19
Well vlc is worse then mplayer xD at the momment I'm compiling mplayer with coreavc from my windows install so hopefully that will help =]

I shall report back!

---

### Post by LowSky on 2009-06-19
how big of a MKV file?
What codec are you using? w32 or w64? because mplayer cannot use w64 and when you force installw32codecs it doesn't work so well.
VLC should wor just fine

I assume when you say full HD rip it comes in at about 10GB in size?

for instance in this included screenshot I have a MKV of Hellboy 2 and its about 8GB I think and has no stuttering or stopping and my computer is just a notch below yours, except my case is better...lol

---

### Post by kamitsukai on 2009-06-19
> **LowSky said:**
> how big of a MKV file?
What codec are you using? w32 or w64? because mplayer cannot use w64 and when you force installw32codecs it doesn't work so well.
VLC should wor just fine

I assume when you say full HD rip it comes in at about 10GB in size?

for instance in this included screenshot I have a MKV of Hellboy 2 and its about 8GB I think and has no stuttering or stopping and my computer is just a notch below yours, except my case is better...lol

it's using the codecs from the mplayer website and then compiled by myself (with lots of help xD) the rip is only 4.6gb in size

---

### Post by kamitsukai on 2009-06-19
Well CoreaAVC works beautifully! I'm now going to hack along to combine it into my my main mplayer build =]

---

