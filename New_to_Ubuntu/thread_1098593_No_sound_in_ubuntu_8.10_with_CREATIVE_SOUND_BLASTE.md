---
title: "No sound in ubuntu 8.10 with CREATIVE SOUND BLASTER 5.1"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by fahadrather on 2009-03-17
hi there..i installed ubuntu 8.10 but i am having sound issues...in fact there is no sound...i am using a creative sound blaster 5.1(no audigy,live,or any thing else)just sound blaster 5.1...i reinstalled ubuntu today but i encounter the same problem...i read somewhere that u need to enter the following codes to make your sound work

sudo killall pulseaudio
sudo alsa force-reload

and then reset everything to ALSA in sound settings. when i did this the sound did work,the sound in rear speakers was too low...but after restart the sound vanished and i had to retype the codes...........i have other issues as well but lets solve one at a time.

---

### Post by thehouseofho on 2009-03-17
After you reset your sound settings in ALSA, type:

sudo alsactl store 0

That will save all of your ALSA settings through sessions and reboots.

---

### Post by fahadrather on 2009-03-17
thanks....there is a small little problem with my speakers...the rear speaker sound is too low...i have creative inspire t6060 speakers...i just restarted the computer....again there was no sound..

---

### Post by wbee on 2009-03-17
fahadrather,

When I was using Windows XP,I used the "add/remove" function to remove the AC 97 drivers from my on board sound,on an MSI motherboard. Then I installed Soundblaster card and drivers which worked fine.

When I went to Unbuntu,I could not get the sound to work----until I went into the bios and disabled the on board sound. Then the alsa drivers loaded on reboot.

((If you use the packaged disk player,go to preferences and set the output to "lossless,cd quality sound".))

---

### Post by thehouseofho on 2009-03-17
Do you have the volume control in your system tray?  I know some people who have added the volume control and all of a sudden everything works.

---

### Post by fahadrather on 2009-03-17
sorry for the late reply.....i disbled on board sound....the sound works now but i get sound only on two speakers(front)..there is no sound from the centre and rear speakers..i tried to adjust them in the volume control but nothing happened

---

### Post by javaholic5 on 2009-03-22
> **fahadrather said:**
> sorry for the late reply.....i disbled on board sound....the sound works now but i get sound only on two speakers(front)..there is no sound from the centre and rear speakers..i tried to adjust them in the volume control but nothing happened
Check out my thread in this link:

[LINK]http://ubuntuforums.org/showthread.php?p=6937251#post6937251[/LINK]

It may help

---

