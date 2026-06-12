---
title: "all music don't won't to play"
date: 2010-08-06
forum: New to Ubuntu
---

### Post by laskarhack on 2010-08-06
i use VAIO VPCEA22EG,when i have installed ubuntu 10.04, but its music player is not running. not even a sound.
can anybody help me? thanx:(

---

### Post by slooksterpsv on 2010-08-06
> **laskarhack said:**
> i use VAIO VPCEA22EG,when i have installed ubuntu 10.04, but its music player is not running. not even a sound.
can anybody help me? thanx:(

Are you unable to play music files, or is sound not working on your computer?

To play restricted formats like mp3, m4a, etc. click on Applications -> Software Center -> Search for: ubuntu-restricted-extras
Install that and restart your music player and you should be able to play those formats.

If it's the other, sound not working let us know so we can help you out.

---

### Post by laskarhack on 2010-08-06
> **slooksterpsv said:**
> Are you unable to play music files, or is sound not working on your computer?

To play restricted formats like mp3, m4a, etc. click on Applications -> Software Center -> Search for: ubuntu-restricted-extras
Install that and restart your music player and you should be able to play those formats.

If it's the other, sound not working let us know so we can help you out.
i have installed *ubuntu-restricted-extra*s but its doesn't work too??
so how?

---

### Post by cjack007 on 2010-08-06
just go to system>> preferences >>sound . 
check under hardware tab if your hardware is recognized by Ubuntu or not.

---

### Post by laskarhack on 2010-08-07
[COLOR=#000000]also do not want, how?[/COLOR]

---

### Post by khelben1979 on 2010-08-08
Try with [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") and check the volume bars to see how that looks like. You might haveto click on some boxes in the sound tab to get it working, such as enable digital sound output or similiar.

---

### Post by Gudkisser79 on 2010-08-08
I do also have a similar problem....Im using ASUS PS5D2-VM motherboard but then my Ubuntu won't let my speaker work out.... Im trying to play a game over the net, yet the music/sound won't come out. What will I do?

---

### Post by simosx on 2010-08-08
Both of you, obtain the full soundcard details with
> 
wget [www.alsa-project.org/alsa-info.sh](www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh


When prompted, say Yes to send the data to alsa-project.org (Alsa website) and post here the URL you will be given. In this way we can see what hardware you have and if there are any problems.

---

