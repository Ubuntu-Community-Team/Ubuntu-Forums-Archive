---
title: "skype webcam"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by panther10 on 2010-10-18
skype  webcam
fed up. Im using ubuntu 9.4 and trying to get skype to work. have a logitec web cam pro 9000/ so far I've loaded pulse audio, alsamixergui gnome alsa mixer. and I've lost track of all the other things. skype will only play back the test sound not my voice and i have no picture. did have it on 9.10 but only voice or picture not both at the same time loaded 10.4 and it just jammed the p.c. "Again" (thats another story) so started over. does anyone know why this is being such a problem. according to logitec and ubuntu it should work out of the box. please i have no more patience and Windows is starting to look a little like an option.. That is a scary way to think..:confused:

---

### Post by Cobracommand0 on 2010-10-18
As far as the mic issue, have you run ```
alsamixer
``` and made sure your mic is turned up/on/boosted if necessary?

---

### Post by HermanAB on 2010-10-19
Howdy,

Try to get your camera to work with a different application first, for example Cheese.  That should ensure that all driver problems are resolved.  If all else fails, install the 'static' version of Skype from the Skype website.

---

### Post by lfforman on 2010-10-19
I had a similar problem with my webcam in 10.10, it worked properly on cheese, and gtalk, but not in skype, the sound was ok, i was able to make calls, but no video.

I installed uvc from synaptics and restarted the system, and it worked perfectly

---

### Post by panther10 on 2010-10-20
this is nuts.. i do have alsa mixer installed as well as uvc. not sure what the static version of skype means.. i installed the latest version twice now.  The wierd thing is i can see and hear the other person and my camera turns on but nothing happens after that and now i lost my typing as well. any ideas??

---

### Post by Lakez on 2010-10-20
Try this [http://ubuntuforums.org/archive/index.php/t-522525.html](http://ubuntuforums.org/archive/index.php/t-522525.html)
maybe there is some useful things here that can get the problem solved

---

### Post by mastablasta on 2010-10-20
> **panther10 said:**
> this is nuts.. i do have alsa mixer installed as well as uvc. not sure what the static version of skype means.. i installed the latest version twice now. The wierd thing is i can see and hear the other person and my camera turns on but nothing happens after that and now i lost my typing as well. any ideas??
 
you have it installed, but did you check the mic setting is up as well as mic boost?
 
type alsamixer in terminal to see the sound settings. set them up propperly and test the mic.
 
 
as for camera try launching skype from terminal with this command:
 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by panther10 on 2010-10-23
okay i now have sound. on that logitec 9000 but no video. i downloaded all the requirements on the  get skype page and then downloaded skype debian.. so im half way through this battle. I know it works because i had it briefly a few weeks ago and then the system crashed and i havent been able to get it back. video comes on when i do a test but just a blank screen

---

### Post by RoddNZ on 2011-05-01
Hi if the code that "mastablasta's" posted runs your webcam in skype from terminal ... then you can paste it into the command line of a skype icon on your desktop or the quick launch panel...

note: add "env" to the start of "mastablasta's" code for it to run in the icon command line...

right hand click on the skype icon select properties and in the popup window you should see a line with "command" beside it... delete the word skype and  paste in the following code

env LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

This runs webcams with skype even in Ubuntu 11.04 I have just had to use it ...

---

### Post by sdowney717 on 2011-05-01
yes, had to do that too. Has to do with Video for Linux version 2 versus video for linux, skype likely only understands VFL not version 2

here is what worked for me
[http://ubuntuforums.org/showthread.php?t=1691647&highlight=skype](http://ubuntuforums.org/showthread.php?t=1691647&highlight=skype)

---

