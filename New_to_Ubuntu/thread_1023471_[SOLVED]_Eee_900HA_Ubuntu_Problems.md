---
title: "[SOLVED] Eee 900HA Ubuntu Problems"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by LoudMetal126 on 2008-12-27
Hello everyone! This is my first post on these forums, though I have been reading them for a while and it seems like a very friendly, knowledgeable place. :)

I just got my Eee 900HA. I love it, its sleek, compact, preforms great. I really want to get this stupid microsoft off of it though, so I decided to go with ubuntu, since I've heard ubuntu is newbie friendly, and I'm completely new to linux. I decided to go with a distributiohn already set up asus's eee pc, so I've narrowed it down to eeebuntu and ubuntu eee (if there's another I've overlooked please tell me). Sadly, after trying the live versions of both, I'm having problems with both. If anyone knows how to fix these, or has any suggestions, I would be VERY appreciative.

Eeebuntu problems:

has scripts to run to fix problems on other eee models, but none for 900HA, and I don't know how to do the fixes myself.

sound problems. I can't get the volume up all the way for some reason. Even if it says I'm at full volume, I can get a louder full volume with windows.

Wifi hotkey unusable.

No idea how to enable/disable webcam (not a priority for me though, as its disabled currently)

Ubuntu Eee Problems:

Same volume problem as eeebuntu, though when I tried to change the sound device, I permanently lost sound.

Wireless hotkey unusable.

During shutdown, screen goes blank, but does not turn off power to system. After pressing [enter] on my system after screen goes blank the system powers off. Does anyone know if this has to do with the common shutdown running linux live where you have to remove the disk then press [enter] to shutdown?


So, those are my problems. I'm very new with linux, but have quite a lot of common sense with computers and think i am a fast learner.
Thanks for reading and I hope you can help. :)

-LoudMetal

---

### Post by LoudMetal126 on 2008-12-28
Ok, so I just installed ubuntu eee and everything's working great! :P

Here's a fix for the audio if anyone else has the same problem.

So, after spending about an hour trying to play around with advanced options for the audio, I finally found the solution in the mixer, and felt like an idiot for not seeing it.

So, first, in the mixer, the audio device needs to be changed to the realtek one. You are then given four volume controls. The master and PCM-2 are the ones we are concerned about. If you have not been getting full volume out of your system, ensure PCM-2 is up at full volume, and your problems will be solved. Hope this can be of some help to somebody. :)

---

