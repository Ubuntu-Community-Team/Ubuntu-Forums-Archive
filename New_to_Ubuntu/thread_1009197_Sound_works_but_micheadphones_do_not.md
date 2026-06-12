---
title: "Sound works but mic/headphones do not"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by MickAld on 2008-12-12
Hiya, I am an absolute beginner in Linux matters having just installed ubuntu 8.10 on my computer as an alternative to windows. Most of the operating system works ok but I am unable to use my microphone and headphones. I think this is a general problem as I installed a version of LinuxMint on a different machine but have the same problem there as well. Can anyone supply me with information on what I need to do to get my machines running correctly. Is it a driver problem and if so how do I install drivers in Linux? The mic and phones I am using use the pink/green sockets. Many thanks if you can give me some advice anyone???

Mick

---

### Post by pedro_orange on 2008-12-12
Do you have it muted? 
Check the alsmixer, and also the volume control. 

9 times out of 10 it's just muted.

Test it using Sound Recorder.

---

### Post by MickAld on 2008-12-12
Tried the mute thing Pedro thx, What is alsmixer?

---

### Post by donkyhotay on 2008-12-12
Alsamixer a program you can install through synaptic that allows you to adjust volume of all the various sound input/output devices on your system. Honestly it's the first thing you should check for any type of sound related problem. If it's installed there should be an entry for it in 
applications > sound & video > alsamixergui
if you don't see that you'll want to install it by typing
```
sudo apt-get install alsamixergui
```
into a terminal prompt (or search for it using synaptic). Once launched take a look through the various volume/mute controls for mic and make certain it isn't at the bottom and the speaker icon has 'sound waves' coming out of it indicating it isn't muted.

---

### Post by JKBurton on 2008-12-12
Hi Mick,

I agree alsamixer is the place to look. If your headphone/mic is USB like mine, then I had the same problem. The standard mixer in Gnome gets confused by USB sound, and confuses what internal volume settings manage what devices.

I personally installed "gnome-alsamixer", but the windowed versaions are all pretty much the same, with small differences in how things are arranged on-screen.

In gnome-alsamixer, each tab represents a "mixer". Start some music playing. Poke around on the different tabs, raising volumes until you get sound in the phones. There's the one that controls your USB devices.

I also had trouble with the default volume control on the panel choosing the wrong mixer at every reboot. You change that thru System/Preferences/Sound, in the "Default Mixer Tracks" section near the bottom.

Best of luck!

---

### Post by MickAld on 2008-12-18
I have managed to detect some response to my microphone now but the level is very low despite adding such things as +20db gain. Is there anything else I need to consider please? Thanks again to those who helped previously.

---

### Post by donkyhotay on 2008-12-18
If you get some response but it's very quiet it has to be a volume issue. Have you tried cranking up the volume on the actual mic entry in alsamixergui rather then just the mic boost +20 option?

---

