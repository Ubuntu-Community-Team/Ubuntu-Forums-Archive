---
title: "Make sounds in Ubuntu 8.10 Louder"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-12-06
It kind of seems like Ubuntu has some sort of hidden limit on how loud my speakers on my laptop will go. Does it? Because my laptop should be able to get about twice is loud as it is now. I have pretty much have to strain to hear it if there is not complete silence in the room and even when their is it is very quiet. How can I fix this?

---

### Post by gettinoriginal on 2008-12-06
What happens if you right click your volume control > open volume control > adjust it from there.

---

### Post by dracayr on 2008-12-06
yeah, check especially for the "pcm" slider when double-clicking on the volume control icon

if that doesn't help, could you give us some more information about your hardware?

dracayr

---

### Post by kansasnoob on 2008-12-06
I like to install gnome-alsamixer. It's in synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video. I always have to crank the first three and last four (via) toggles up to about 90%+.

---

### Post by Panzor on 2008-12-06
$alsamixer
Adjust the master and PCM volume and you should be quite loud. The PCM volume doesn't get adjusted from the GUI stuff as far as I know, and puts a limit. Lower seems to have better quality, but has a lower volume. I like mine around 90%.

---

