---
title: "sudden sound failure"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by FallFromGrace on 2009-02-12
Booted up the computer today (, and was playing an old CD on it with Rhythmbox. I closed Rhythmbox by accident and tried to play the CD again, but suddenly, nothing plays --- I don't only mean that no sound comes out, but pressing the 'play' button doesn't result in the forward movement of the little box that indicates where you are in the song. It was playing fine before (.wav format), so it's not a CD issue.

Checking around it also appears that system sound is gone from my computer; tried playing things that worked fine yesterday, like clips from Youtube, and tried testing sounds in System -> Preferences --- nothing. I'm completely new to Linux so while I'm aware of system logs and how to find them I have no idea what any of that means.

Help?

---

### Post by jenkinbr on 2009-02-13
In System > Preferences > sounds, check to see that everything is set to ALSA (do take note of what the settings are before changing them).

---

### Post by sydbat on 2009-02-13
If jenkinbr's suggestion has no effect, try:

Applications > Accessories > Terminal

```
killall pulseaudio
``````
sudo alsa force-reload
``````
pulseaudio -D
```This should reset your audio to normal.

---

