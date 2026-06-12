---
title: "I Want sounds to appear in my Earphones"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Webster12 on 2011-03-06
Hi everyone,

I have read a lot of post regarding this issues and have many of the steps they had suggested but nothing seemed to work. 

I have a Lenovo G460, card is HDA Intel and the chip is Intel Ibexpeak HDM. I have tried the alsamixer as per other tutorial I should see a headphone on the menu but nada. What to do?

Thank you in advance.

---

### Post by maqtanim on 2011-03-06
Can you hear the sound with Laptop's built in speaker? Did you install Ubuntu-restricted-extras?

---

### Post by Webster12 on 2011-03-06
Yes I can hear the sound on the built in speaker. And I believe I pretty much installed all the restricted media repositories. Is there somewhere I can check if I did? Thanks

---

### Post by metalf8801 on 2011-03-06
1. Can you post the links to what you have tried or even better just tell us what you have tried?

2. Are you sure the headphones you are using work? Have you tested them on another device?

---

### Post by Webster12 on 2011-03-06
1.) I've tried this:

[http://ubuntuforums.org/showthread.php?t=1597218](http://ubuntuforums.org/showthread.php?t=1597218)

and some others, I tried to install & uninstall the alsamixer and yesterday tried install uninstall alsamixer and pulseaudio...

2.) yes, my headphones work, it does with my ipod and nintendo.

Most of the stuff that I've tried are for other brands, and I am not sure how that would fair but ive tried and it didn't work...

thanks,

---

### Post by lidex on 2011-03-06
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=intel-alc889a" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Pretty much a guess, from the limited information you provided. If that doesn't work remove
```
options snd-hda-intel model=intel-alc889a
```
from
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
and reboot. Then use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by Chronon on 2011-03-06
Did you check the sound level using alsamixer?  Certain channels seem to default to off in my setup and I have to raise them again if I reboot.  (Line in and headphones for me)

---

