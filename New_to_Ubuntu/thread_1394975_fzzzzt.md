---
title: "fzzzzt"
date: 2010-01-31
forum: New to Ubuntu
---

### Post by muncy on 2010-01-31
Bit of a strange one. I have just bought a compaq cq61 and installed 9.10 on it. When I shut down there is a fzzzzt sound from the speakers. It doesn't matter whether the volume is turned up, I still get the rather worrying noise. The laptop came with Windows Vista pre-installed and I never get this sound when shutting down on the windows side.

Any ideas?

---

### Post by audiomick on 2010-01-31
That is probably the sound system shutting down. I think it is pulse audio that is standard. I don't know for sure, because my system is a bit of a hybrid between standard and Ubuntu studio.

Mine makes a nasty click at start and shutdown, and I have read a number of posts indicating similar behaviour. I think it just doesn't start and shut down very cleanly. I don't know if anything can be done. It most likely wont directly damage anything. I certainly hope that something will change with that in the near future, because it isn't really acceptable. If I had my Genelec speakers attached to the computer, I would be concerned.

---

### Post by ajgreeny on 2010-01-31
There have been several reports of sound problems, noises etc, on machines with HDA sound cards.  I think that may be true of your laptop so these are two possible solutions:-
> I have tested this with a fresh install of the release version of Ubuntu 9.10 desktop 64bit. The clicking / popping still exists.
 I can confirm that editing the file /etc/modprobe.d/alsa-base.conf and changing the following line fixes the problem:-
   options snd-hda-intel power_save=10 power_save_controller=N
to
  options snd-hda-intel power_save=0 power_save_controller=N

or
> However the problem vanishes if the line

options snd-hda-intel power_save=10

is commented out in /etc/modprobe.d/alsa-base.conf as a workaround.

---

### Post by audiomick on 2010-01-31
Hallo ajgreeny,
I _think_ that those were related to apparently ramdom clicking noises when the computer is running. It is the same phenomenum, i.e. the sound system doesn't shut down cleanly. The clicking comes from the power save function shutting down the sound card. The changes you quoted prevent that, and thereby the "random" clicking noise. I doubt that those changes will have an effect on the shutdown behaviour. But I could be wrong...;)

---

### Post by muncy on 2010-01-31
Hi you two

Thanks for the replies. I can confirm that neither of the options resolve the issue when shutting down. As you say Audiomick, hopefully it will get fixed in a bug release, until then your replies gives me confidence that my laptop is not about to explode!

---

