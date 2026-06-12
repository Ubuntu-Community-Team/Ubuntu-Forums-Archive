---
title: "playing videos problem"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by shaullx on 2008-12-29
whenever i play a movie the movie works but it sort of jumps all the time and i get sort of black or sometimes white strips on the movie
tried in the default player of ubuntu 8.10 and with mplayer and with vlc(it doesnt require codecs so it can't be a codec problem)
my video card driver is installed and working
please help?:P

---

### Post by wolfen69 on 2008-12-29
disable or remove the video driver and see if that helps. if it is OK after that, then you know where the problem lies.

---

### Post by shaullx on 2008-12-29
btw in full screen it stops blinking after a few seconds but still it's anoying how can i slove this? :o

---

### Post by sharon.gmc on 2008-12-29
I am also having problems with playing movies.  It stops.  When I restart, it stops again in the same part.

---

### Post by shaullx on 2008-12-29
ok well i found the problem
seems that ati + compiz making problems over videos
turned off effects and now its ok
is there a particulare effect that causing this?

---

### Post by 2hot6ft2 on 2008-12-29
Compiz is graphics intensive so is playing videos. Compiz can slow your frame rate so can videos. In short it's not 1 compiz effect and it's best to turn compiz off when playing videos or graphic intensive games.

---

### Post by blueridgedog on 2008-12-29
Setting visual effects to none solves this for me

---

### Post by fooman on 2008-12-29
> **shaullx said:**
> ok well i found the problem
seems that ati + compiz making problems over videos
turned off effects and now its ok
is there a particulare effect that causing this?

i fiddled around with the compiz and nvidia settings until i finally got the flashing/flickering lines to cease.  not sure what exact setting it was,  but some of the things i set were:

in nvidia-settings > xserver xvideo settings > put a check next to "sync to vblank"

in compizconfig settings manager > general options > display settings > put a check in "sync to vblank", set the refresh rate to the same as in my nvidia settings....and i replaced the value in "outputs" from "640x480+0+0" to my actual resolution: 1680x1050+0+0

the flickering lines have gone away and i still have the visual effects on "extra". :D

---

### Post by shaullx on 2008-12-30
> **fooman said:**
> i fiddled around with the compiz and nvidia settings until i finally got the flashing/flickering lines to cease.  not sure what exact setting it was,  but some of the things i set were:

in nvidia-settings > xserver xvideo settings > put a check next to "sync to vblank"

in compizconfig settings manager > general options > display settings > put a check in "sync to vblank", set the refresh rate to the same as in my nvidia settings....and i replaced the value in "outputs" from "640x480+0+0" to my actual resolution: 1680x1050+0+0

the flickering lines have gone away and i still have the visual effects on "extra". :D

i have ati but i will try later tnx

---

