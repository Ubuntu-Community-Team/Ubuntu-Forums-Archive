---
title: "Sound From Headphones and Speakers"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by wordsmith64 on 2010-09-09
Greetings!

I'm a relative linux newbie, and have been using Ubuntu since 8.04 but have never really needed to dig around "under the hood".

The problem I am having has to do with a fresh install of Ubuntu 10.04, when I plug in a set of headphones, my laptop's external speakers aren't muted and keep playing. I've read through a few other solutions but none of them have worked for me. Here is some information about my system I got from the alsa mixer.

Model: Toshiba Satellite L655-s5062
Card: HDA Intel
Chip - Conextant ID 5069

Any help with this problem would be greatly appreciated, as this is the only problem I have with an otherwise excellent OS. Thanks for reading!

---

### Post by Tr0Y_L33 on 2010-12-07
i have same problem like you and i use this way to solve this problem.....

goto this page and follow step by step.....

[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

i hope, it can solve your problem too..

---

### Post by canucked on 2010-12-09
If using Tr0Y_L33's suggestion of updating your alsa modules doesn't work for you, perhaps this will.

I configured a Toshiba Satellite L655-S5115 for a friend.  By running this in Terminal:
```
cat /proc/asound/card0/codec#* | grep Codec
```
... I found out that the laptop uses Conexant CX20585.

This is the solution that worked for me:
Edit /etc/modprobe.d/alsa-base.conf and add:
```
options snd-hda-intel model=thinkpad
```

I created a thread further explaining that laptop's issues:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

Good luck!

---

