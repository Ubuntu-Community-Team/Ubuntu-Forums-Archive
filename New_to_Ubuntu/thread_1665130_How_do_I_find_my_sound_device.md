---
title: "How do I find my sound device?"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by inf4nticide on 2011-01-11
I'm trying to get this metronome program to work (Gtick), but it's pointing to /dev/dsp for my sound output. I have sound, but /dev/dsp does not exist on my computer...how can I find out where to point the program?

---

### Post by TeoBigusGeekus on 2011-01-12
Try /dev/audio.

---

### Post by matt_symes on 2011-01-12
Hi

GTick uses oss (/dev/dsp) and that is deprecated. To get around it install alsa-oss either from synaptic or from the terminal

```
sudo apt-get alsa-oss
```

Enter your password. You will not see it echoed to the screen.

Then start gtick from the command line (or using ALT F2) by typing 

```
aoss gtick
```

If that fixes it, create a launcher.

Kind regards

---

### Post by inf4nticide on 2011-01-12
Thanks matt, that did the trick

---

### Post by inf4nticide on 2011-01-12
Well, that got my metronome working, but now TuxGuitar is broken again (I fixed it the first time by installed Timidity, but now it emits no sound no matter what)

---

### Post by TeoBigusGeekus on 2011-01-12
Oss has been known to cause problems (lock ups) to pulseaudio and alsa.
Are you trying to run tuxguitar while you have gtick open?

---

### Post by garyhibdon on 2011-01-12
try this then, it may be a fix all to both issues

```
 sudo apt-get install alsa 
```


may not do the trick, but always worth the effort

---

### Post by matt_symes on 2011-01-12
Hi

> Well, that got my metronome working, but now TuxGuitar is broken again (I fixed it the first time by installed Timidity, but now it emits no sound no matter what)

Hmmm. Isn't that always the way :( Which version of the TuxGuitar plugin did you install? There are three in the repository; One for oss, one for alsa and one for jsa.

BTW: How did timidity fix TuxGuitar ?

Kind regards

---

### Post by inf4nticide on 2011-01-12
Timidity USED to give me an option to use it as a MIDI port in TuxGuitar. Now it doesn't show up...it seems it can't find a usable midi port. And yes I have the alsa plugin installed.

---

### Post by matt_symes on 2011-01-13
Hi

Try the oss plugin. 

BTW: That should be alsa oss emulation plugin i think (i hope). 

If it does not work you can remove the plugin later.

I don't actually use TuxGuitar, but i may try to install and get it working in a VM with GTick if you cannot get it working with the oss plugin.

What version of Ubuntu do you use ?

Kind regards

---

### Post by inf4nticide on 2011-01-13
Well, the OSS plugin is active, and the only midi port available comes from the Alsa plugin being active. I don't understand, there used to be 4 timidity midi ports and now there are none, now I have no sound....


I use 10.10

---

