---
title: "Master volume does not control headphones"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by st130811 on 2009-07-31
Originally, my headphones had no volume at all. After trying a bunch of things, I found a switch under the volume control called "Duplicate Front" that allowed my headphones to have volume. But, now the Master Volume does not control the headphone volume. 
Reading some other threads, I've been able to get the keyboard to control both, but using the volume icon doesn't control the headphones. 
Under "System>Preferences>Sound" there is no headphone option, but I determined that "PCM," "Surround," and "VIA DSX" each can control the headphone volume. I have all of them highlighted, as well as the "Master" option. That is what allowed the keyboard buttons to control both Master Volume and my headphone volume. It still didn't allow the volume icon to control the headphone volume.

In case it makes a difference, I am using Ubuntu 9.04 on a laptop.

---

### Post by kansasnoob on 2009-07-31
I always like to install gnome-alsamixer either using Synaptic or you can install using the Terminal:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]123079[/ATTACH]

---

