---
title: "No Sound in Karmic"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Cooter2543 on 2009-11-19
When I first installed 9.10, my sound worked. Now all of the sudden it stopped working.

In the Hardware tab in System> Preferences> Sound, it shows I have:

CA0106 Soundblaster
1 Output
Analog Surround 5.1 Output

Internal Audio
1 Output/ 1 Input
Analog Stereo Duplex

In the Output tab, I have the CA0106 Soundblaster selected for sound output. My speakers are hooked up to the soundblaster card, but no sound at all anymore. Nothing is muted, so I can't figure out why I can't get sound.

Edit: I also tried my internal audio with no luck either.

---

### Post by Cooter2543 on 2009-11-21
Nobody can help?

---

### Post by camaron1 on 2009-11-21
Copy and paste this on a terminal: 
**gksudo gedit /etc/pulse/default.pa**
Give your password when prompted.

On the text editor go to preferences and choose to display line numbers. On line 45-46 you should probably see:
45 # load-module module-alsa-sink
46 # load-module module-alsa-source device=hw:1,0

Remove the sign **#** from both. Save the document and reboot.

If this doesn't help, just go to **Synaptic** and remove **pulseaudio** which is -with all likelihood- causing the problem.

---

### Post by Cooter2543 on 2009-11-22
Thanks so much! That did it!

---

