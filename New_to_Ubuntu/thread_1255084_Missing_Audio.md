---
title: "Missing Audio"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by mbrinskelle on 2009-09-01
I just installed Ubuntu:Jaunty today and am having audio issues. I have a Asus K8U-X Series motherboard. Usually when i reformat i have to install the audio drivers for the onboard sound and I cant figure out the wayt o set that up on Ubuntu. If anyone could help i would appreciate it.

---

### Post by mapes12 on 2009-09-01
I add the non free packages to get all media working:

1. Synaptic - search for ubuntu-restricted-extras and install it

2.Then visit [Medibuntu]("http://www.medibuntu.org/") and follow the instructions in the Repository HowTo section. Basically, it's just cutting and pasting commands into Terminal

All your media e.g.mp3, DVD's etc. should then play OK.

---

### Post by 3rdalbum on 2009-09-01
> **mbrinskelle said:**
> I just installed Ubuntu:Jaunty today and am having audio issues. I have a Asus K8U-X Series motherboard. Usually when i reformat i have to install the audio drivers for the onboard sound and I cant figure out the wayt o set that up on Ubuntu. If anyone could help i would appreciate it.

Usually, audio drivers are available out-of-the-box. If you're not getting any sound, try right-clicking on the volume control applet, go to Volume Control and turn up the PCM, Master and Front channels.

---

### Post by mapes12 on 2009-09-01
If you have the codecs installed per post #2 then go to Terminal ```
alsamixer
``` You should be able to tab around and increase volume with your up and down arrow keys.

---

