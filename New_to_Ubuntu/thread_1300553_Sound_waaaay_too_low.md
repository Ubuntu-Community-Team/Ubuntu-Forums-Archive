---
title: "Sound waaaay too low"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by Don Andi on 2009-10-25
Hi,
I used to have ubuntu 9.04 and today I upgraded it to 9.10 through the update manager.

At first, I had NO sound, but then I followed a guide which told me to do the following:

```
sudo aptitude install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras
sudo aptitude remove libpulsecore9 pulseaudio pulseaudio-esound-compat pulseaudio-module-hal pulseaudio-module-x11
sudo aptitude dist-upgrade
```Now it's very low and I can't see a sound mixer on the panel and alsa-mixer also ain't work, so I cant make it any louder.

Would be glad if someone could give me some help ;-)

---

### Post by quinnten83 on 2009-10-25
Hey, 
try left clicking on the sound icon on the panel, and choosing the last tab.

---

### Post by Don Andi on 2009-10-25
There IS NO ICON.

---

### Post by quinnten83 on 2009-10-25
also no icon under " system > prefferences > sound"?

---

### Post by Don Andi on 2009-10-25
there is something but it just tells me that its waiting for the soundsystem and closes

---

### Post by quinnten83 on 2009-10-25
Sounds more like a problem with your soundsystem getting recognized.
I don't think I can help you much with this.
you could run an lshw or lspci to check wether linux sees your souncard.
and then take it from there. 
I know you could run sound-config from the terminal, but that was when we didn't have pulse audio.
try installing padevchooser (pulse audio device chooser, perhaps you can configure one or the other with it.

---

### Post by Don Andi on 2009-10-25
still nothing, thanks anyway. i hope theres gonna be an update which fixes this soon

/edit fixed: I reinstalled karmic using the cd and now it works.

---

