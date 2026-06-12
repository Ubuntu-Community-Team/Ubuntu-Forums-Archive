---
title: "No sound Ubuntu 9.04 NOVICE NEW USER"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by linnovice on 2009-10-25
Hi all, im a total novice. I have pretty basic computer skills, like linux and have installed ubuntu 9.04 i have managed to configure it to play videos etc but i have no sound . I have an idt high def soundcard on a hp pavillion dv6 laptop.

I have no windows just linux

can anyone help? With an easy checklist of what i need to get sound?

I have alsa gnome mixer and pulse audio installed

thanks
bj

---

### Post by laidback on 2009-10-25
This may help.

Top right of your desktop is the volume control (picture of a speaker). Drop it down and you'll see a button called "Volume Control...", press that and you'll see "Alsa Mixer". Now depending what's on display you may see controls for Speakers, or Front etc. You need to activate the appropriate one by clicking on the speaker button at the bottom in order to remove the red cross symbol. Also adjust the volume up towards maximum.

If the appropriate control doesn't appear press Preferences and select the one(s) you want.  

Now increase the volume(s) and try again.

---

### Post by dv3500ea on 2009-10-25
This is a common problem with the hp dv3 laptops - but fortunately it can be fixed.
Try running this (ALT-F2):
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```Then add this line to the end
```
options snd-hda-intel model=hp-m4 enable_msi=1
```
If that doesn't work, try replacing hp-m4 with hp-dv5 or hp-dv6.

---

