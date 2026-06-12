---
title: "speaker and headphone work at same time problem"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by samizdatstudio on 2011-05-04
my fujitsu u810 have the some problem,
when i wanna listen music from headphone,speaker and headphone function at same time,it havent change each other,
i no install any additional driver for sound card
is it need install alsa?
where i go change this or fix it?
thanks

if any one know,please help

---

### Post by yonathaniel on 2011-05-04
This problem is a pain in the butt. I have the same problem in my Asus X70IJ.

In the previous release I managed to fix this by editing ```
/etc/modprobe.d/alsa-base.conf
``` and adding the line ```
options snd-hda-intel model=asus-laptop
``` (or something like this), but this doesn't work anymore afaik. More detailed instructions here:
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

One solution I've considered is to get USB headphones. atm if I want to listen to something I need to rig headphones to my Zoom H4, which works as a USB device for audio output (and input). This allows me to bypass the internal soundcard and the driver that doesn't work.

---

### Post by samizdatstudio on 2011-05-04
so it maybe sound driver problem?
i try the sound card model use with 

options snd-hda-intel model=fujitsu

it not work,and internal mic not work too.

hope someone help

---

