---
title: "Pandora is just a giant brown box in firefox"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-06
hey all,

i have just upgraded my flash support and it still doesnt work. 

if i open pandora.com, everything shows up at first and it says "pandora is loading". 
when it gets to the first song on a station, it will hesitate and then immediately skip to the next song. 
when it gets here, firefox fades to black as it freezes. it will then, after a minute or so, unfreeze with a giant brown rectangle covering up the player. 
and i hear nothing. 

pandora works on my laptop just fine. anyone have any ideas???

---

### Post by skymera on 2009-04-06
Hi

Do you run 32bit or 64bit Ubuntu?

If you run 64bit download the latest Flash from Adobe , don't use the one from the repos.

---

### Post by JC Cheloven on 2009-04-06
A bit out of topic but still: 
Sadly, pandora isn't available outside usa any more :-(

---

### Post by asuastrophysics on 2009-04-06
i'm using 64-bit and all the other flash pages are displaying just fine. it's like pandora has trouble getting audio to play through the browser. 

when i ran firefox in terminal, i got "segmentation fault"

---

### Post by brandoncolorado on 2009-04-06
could you try another browser like opera?  

try restarting?

try clearing cache completely and restarting?

Just some ideas.

---

### Post by asuastrophysics on 2009-04-06
i downloaded galeon and got the same result, only galeon had to be forced-quit after going to pandora.com

....am i missing a codec here?
is there a list of codecs i might need somewhere to make this work?

---

### Post by asuastrophysics on 2009-04-06
i get the same result in opera as well, except no brown rectangle appears. none of the stations are clickable, and none of the flash buttons work. right now it says it's playing "better man" by pearl jam. 

i dont hear anything though, and it's been sitting on the same song for over an hour. does anybody else except me seem to be having problems with pandora?

---

### Post by asuastrophysics on 2009-04-06
oh wait, i figured out why. i have no sound in youtube either. 

it seems as if i *have* to use (sighs, here we go again) pulseaudio.

i had uninstalled it for a reason. it was unstable, it made rhythmbox crash for no reason, and it would sometimes crash and ubuntu would fall back to alsa - in the middle of a playing song.

so everyone knows, you have **no choice** but to use pulseaudio, if you wanna hear sound from firefox

unless of course, someone could kindly tell me how to enable sound in firefox with alsa?
:D

---

