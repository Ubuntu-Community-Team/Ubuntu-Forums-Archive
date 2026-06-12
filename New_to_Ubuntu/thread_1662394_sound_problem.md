---
title: "sound problem"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by Mayank Bhagat on 2011-01-08
When I had windows i had to install realtek sound driver for the sound to work
What do I have to do in Ubuntu to get it working?

I dont have a sound card

Note: I was able to here the front centre audio

---

### Post by I8NY on 2011-01-13
Install Alsa.  It is a older linux audio driver but works a lot more.  In the terminal type: ```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get install alsa-base linux-sound-base alsa-utils
sudo apt-get install gnome-alsamixer 
```

---

