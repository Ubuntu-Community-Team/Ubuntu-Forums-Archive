---
title: "Sound card issues"
date: 2010-11-29
forum: New to Ubuntu
---

### Post by Nahjil567 on 2010-11-29
So I have been getting the hang of ubuntu but I am still a massive noob. I don't want to break anything messing with this, but I have a n-force 2 chipset with a built in sound card. The alsa web site states the driver being AC97. It works on the outputs on the back of the desktop leading to my monitor. There is a microphone in and a headphone on the front of the pc that is not. Has anyone had a similar issue? Clarification: I would like to be able to plug in my headphones and stop the sound from being played on the monitor speakers, and would like to have my microphone working as well.

---

### Post by Nahjil567 on 2010-11-29
bump

---

### Post by khelben1979 on 2010-11-29
In the [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") application you can adjust the volume bars for the things which is attached to your computer.

For a working microphone, the easiest thing is to attach a USB headset and if that's not a solution for you, then you can take a look at the sound server [PulseAudio]("http://en.wikipedia.org/wiki/PulseAudio").

---

### Post by Nahjil567 on 2010-11-29
Ok So I used the alsa mixer application and got it to play through my headphones the issue becomes it is also plays through the speakers. Is anyone aware of a way to set up the mixer to recognize when the headphones are plugged in and to mute the speakers when that occurs?

---

### Post by khelben1979 on 2010-11-29
The Linux system cannot detect if you have plugged in your headphones or not, unless it's by [USB]("http://en.wikipedia.org/wiki/Usb") or similiar a.f.a.i.k.

---

### Post by Nahjil567 on 2010-11-30
Well then thank you for your time.

---

