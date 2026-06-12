---
title: "why is aduacios not working at all ????"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Drakkor on 2009-04-12
Yeah, it used to  work just fine,but recently it loads a playlist,and I hit play, but nothing happens, reinstalled also ! :mad:

---

### Post by taavikko on 2009-04-12
Try removing it's config file on /home

Can't remember if it's on ~/.config/audacious/
or just ~/.audacious

If it doesn't help. start the app in terminal and post the output

---

### Post by Drakkor on 2009-04-12
Thanks for the reply, taavikko
Yeah I removed the .config file,but it still didn't work.
You know,thinking back, this may have been related to a Skype audio
problem,I had a few weeks ago, I changed the audio somehow,but can't 
remember what it was. 

Here's the output:

---

### Post by taavikko on 2009-04-13
Have you tested various audio-output modules in audacious preferences.
Note: some changes requires app to be restarted.

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)
There's some good tips concerning on audio on apps.

Also psyke has written tutorials to get sound working
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Drakkor on 2009-04-13
Yep,preferences did it ! :p
It was set for PulseAudio plugin,which,if I remember didn't play well
with Skype, I selected the Alsa Audio plugin,and it works just fine !
Thanks !

---

