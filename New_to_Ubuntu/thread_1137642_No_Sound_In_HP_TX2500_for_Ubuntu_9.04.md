---
title: "No Sound In HP TX2500 for Ubuntu 9.04"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by linuxneeewb on 2009-04-25
I installed a fresh Ubuntu 9.04 64 bit edition, and sound simply will not work. The computer is a HP TX2500 tablet PC. I was able to get sound to work in Ubuntu 8.10, but not now. I cannot hear the login sound or any sound for that matter be it on a website or in a music file. I would appreciate any and all help in fixing this matter. 

:guitar:

---

### Post by Fughley on 2009-04-25
darn it! I was hoping somebody answered you back already- I just loaded 9.04 onto my HP DV6-1030us laptop and no sound what so ever! Arrggh! 
I will be watching to see what pops up.

---

### Post by Favux on 2009-04-25
Hi linuxneeewb,

Did you check that at the bottom of the file "/etc/modprobe.d/alsa-base" you still have the following line?:
```
options snd-hda-intel index=0 model=toshiba position_fix=1
```
Also a lot of people are reporting that the mixer is muted when they install Jaunty.  Make sure the sliders are up.

---

### Post by linuxneeewb on 2009-04-26
Well thanks. That seems to have worked. Interestingly when I used the command:

gksu /etc/modprobe.d/alsa-base 

it failed to load the file. I had to use: 

sudo pico /etc/modprobe.d/alsa-base 

in order to paste the additional line that you said to put in. 
Thanks again

---

### Post by Favux on 2009-04-26
Hi linuxneeewb,

Your welcome.

I think you would have wanted:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
This uses the graphical sudo with the graphical gnome-editor and avoids permission problems.

---

