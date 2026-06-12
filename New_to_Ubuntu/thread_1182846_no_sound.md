---
title: "no sound"
date: 2009-06-09
forum: New to Ubuntu
---

### Post by Reymond on 2009-06-09
[COLOR=Black][SIZE=2][/SIZE][/COLOR]Hi, guys I've just shifted from windows xp to ubuntu 9.04 few days ago. Everything was  going perfect. Then I became a little more adventurous & started experimenting with gnome applications (e.g appearance,display,sound,remote desktop etc). I think somewhere there I've disabled something which I can't remember now & afterwards I can't hear any sound (all audio hardware connections are perfect) in desktop.Although login sounds are available. ....... Help.

---

### Post by jenkinbr on 2009-06-09
Check your sound settings.  Go to System >> Preferences >> Sound

Select alsa for all options, then try to play the test sound.  if that doesn't work, try setting all to autodetect and try playing test sounds again.  If that still doesn't work, reset all settings to alsa, close the window, and open Applications >> Accessories >> Terminal, run```
aplay -l
``` and post the output of that command here.  you may be haveing similare issues to what I am experiancing.

---

### Post by Reymond on 2009-06-09
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by jenkinbr on 2009-06-09
There appears to be some issues with the Intel HDA deveices - I've yet to come across a solution to this, but stay tuned...

I've heard it could be INTEL HDA +nVidia Gfx card issues
I've heard it could be an alsa-base issue.

some things you might try:
[Pulseaudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Johan-Steyn on 2009-06-09
Hi Reymond,

There are a few ways to restore your sound to it's original settings.

Jaunty is released with Pulseaudio 0.9.14. 

There is a Jaunty Sound Solutions guide at this thread: 

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Hope it helps.

Regards,

JS

---

### Post by jenkinbr on 2009-06-09
I may have to try that as well - thanks.

---

### Post by Reymond on 2009-06-10
:D  Thank u guys, problem solved.

---

### Post by jenkinbr on 2009-06-10
Wow - now I really have to try it.

maybe I didn't need to order that usb sound card after all...

---

### Post by andrewmoquin09 on 2009-06-10
Hi, I'm Andrew..

I'm just new here and tried to join the discussion but it seems that you already solve the problem. Congrats to all!

---

