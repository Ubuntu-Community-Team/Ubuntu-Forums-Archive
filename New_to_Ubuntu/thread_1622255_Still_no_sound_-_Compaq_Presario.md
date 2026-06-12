---
title: "Still no sound - Compaq Presario"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by Javelin Dan on 2010-11-15
I recently went to the archives here and downloaded instructions to fix a problem others shared of having sound with earphones but not through the speakers of my Compaq Presario laptop. I followed directions for "adding ppa" with the Synamptic Manager. Everything went according to plan until I was instructed to re-open Synamptic Manager, click on "Search", and select the "linux-alsa-drive-modules" package. When I do this search, it shows no package exists. I have downloaded "Alsa Mixer" and "Alsa Player" but appearently no drivers exist. Can I download these separately or is there something I'm missing? Thanks.

---

### Post by onaridge on 2010-11-15
Are you 10.10 or 10.04. I have 10.04 and had to install the latest ALSA driver configuration files from the Unstable PPA and download via the software center. My problem was different but if it's the newest drivers you need, that's where they are. This fixed my problem.

---

### Post by Javelin Dan on 2010-11-15
This installation is a year old. I know it's "Karmic" something or other, but am not in front of it and am not sure of the version #. (9.1?)

---

### Post by lkraemer on 2010-11-15
Maybe this will help.

I have a Compaq Presario CQ61-225EO, and I had sound through headphone jack but not from speakers.

The following solution fixed my audio problem in both Jaunty (9.04) and Karmic Koala (9.10).


To do this open this document in your text editor APPLICATIONS -> ACCESSORIES -> TEXT EDITOR

Then also open a Terminal window APPLICATIONS -> ACCESSORIES -> TERMINAL

Copy and paste the next line in the Terminal window, then press the ENTER KEY.

sudo gedit /etc/modprobe.d/alsa-base.conf


At the end of the file, copy and paste these lines at the end of the file,
then save the file.  Next time you re-boot maybe you will have sound.


options snd slots=snd-hda-intel
options snd-hda-intel model=hp-hdx
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1 


lk

---

### Post by Javelin Dan on 2010-11-15
THANKS! I'll try anything at this point, and that sure sounds easy enough. I'll have to wait till later tonight to try it, but I'll let you know of the outcome either way. Thanks again!

---

