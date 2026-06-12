---
title: "someone explain how to do this...."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by amiacamal2 on 2009-09-09
i have an acer aspire 6935g. with ubuntu i have no sound. apparently sound works if i...

"install latest alsa-driver snapshot and set model=acer-aspire-8930g"

problem is im ubuntu-illiterate so... someone help??

---

### Post by fishy6969 on 2009-09-09
Try - 

Step 1: Open Terminal from “Applications&#8594;Accessories&#8594;
Terminal”

Step 2: Run the following commands (copy/paste each command into the Terminal and then hit <enter>)

sudo gedit /etc/modprobe.d/alsa-base

Add these 2 lines to the end of the alsa-base file:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Don't forget to reboot your pc after every change you make on the /etc/modprobe.d/alsa-base file.

If the previous alsa-base options don't work, please try these 2 lines instead:

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=acer-aspire

---

### Post by executorvs on 2009-09-09
second the above post. it worked on my father's acer and it is virtually the same as yours. I did not have to install anything other than the standard updates from synaptic and then alter alsa-base.conf .

after that some of the audio settings were turned down.
to fix this click on the speaker icon in the top right of your screen. select volume control and then check preferences for OSS, ALSA,and pulse audio to make sure all of the pertinent sound channels are displayed.
then finally maxing all the sliders.

---

