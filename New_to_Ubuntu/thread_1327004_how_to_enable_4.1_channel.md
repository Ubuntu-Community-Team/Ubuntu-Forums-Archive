---
title: "how to enable 4.1 channel"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by a-5-h@hotmail.com on 2009-11-15
hi, i'm using ubuntu 9.10 and only 2 channel are working. i've try "gnome-volume-control"
and it 

Hardware: 1 output/ 1 input  Anlalogue stereo duplex.
Output:  Internal Audio Analogue stereo stereo


before i was using ubuntu 9.04 and i was getting 4.1 the problem arises when i upgrade to 9.10. 

my motherboard is asrock 945GC.  

can anyone please help me...

thank..

---

### Post by prshah on 2009-11-15
> **a-5-h@hotmail.com said:**
> hi, i'm using ubuntu 9.10 and only 2 channel are working. 

You need to use "alsamixer" to set the alternate line-outs.

Pulseaudio runs "on" alsa, and alsa needs to be set up properly. 

You can get alsamixer (and alsamixer-gui) from the repositories.

Use this, change "mic" to "line out" and "line out" also to "line out" (Though already marked as "line out" you need to change it to something else and then back to "line out").

If you don't find these settings in alsamixer(-gui) then your ALSA setup needs work; eg, I had to load snd-hda-intel (sound card driver module) with the options "model=3stack" before I was offered the options to reassign jacks.

---

### Post by a-5-h@hotmail.com on 2009-11-15
thanks.. i've used the command " $ alsamixer " and set it to 6.

---

