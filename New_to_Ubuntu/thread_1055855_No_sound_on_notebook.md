---
title: "No sound on notebook"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by ersatzorama on 2009-01-31
I'm having a really hard time getting my sound to work on Ubuntu. I only recently switched and I'm still learning the basics of working in this new OS. 

Anyway, I updated my ALSA drivers to version 1.019 with [this]("http://http://ubuntuforums.org/showthread.php?t=1046137") script. I'm on Ubuntu Intrepid, kernel 2.6.27-7-generic. I'm on a Dell M1530, soundcard is a Intel STAC92xx. 

I tried disabling PulseAudio, switching all my devices to the ALSA in Sound Preferences, checking no channel is on mute in the Gnome Mixer, but all seems fine and has no effect whatsoever. The sole thing that makes my sound work, though, is the operation:

```
sudo alsa force-reload
```

From then on everything (well, as far as I checked) works fine. Until I reboot and my notebook stays silent again. Is there anyone who has a suggestion for a new move?

---

### Post by theozzlives on 2009-01-31
I dunno if this will work or not but try editing /etc/modules and for the last line put:
```
snd-Intel STAC92xx
```
or a variation thereof.

---

### Post by ersatzorama on 2009-01-31
Ok, I think I figured it out. To the /etc/modules file I added

```
snd-had-intel
```

Then to /etc/modprobe.d/alsa-base I added

```
options snd-hda-intel model=ref
```

The sound is a bit on the soft side in my opinion (with all devices up to 100, except the master, which is around 80), but I'm comparing to my Windows configuration here, so it might not be fair. 

But I got sound! Yay! 

Thank you theozzlives!

---

