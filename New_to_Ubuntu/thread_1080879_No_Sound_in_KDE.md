---
title: "No Sound in KDE"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Unanimated on 2009-02-25
I had my sound working perfectly in Ubuntu, but I switched over to Kubuntu 8.04 tonight. My Ubuntu was 8.10. I had an 8.04 installation of Ubuntu, with sound working perfectly, then I upgraded, and it still worked. There is no sound in Kubuntu - I tried installing Pulseaudio, but it doesn't even recognize an audio stream. I don't understand how the Sound panel in preferences is supposed to work. I have two sound cards - an Audigy and a VIA one that is built into my motherboard. I'm using the Audigy - or at least, I should be. Any help?

I've tried plugging it into the VIA Tech. one, to no avail. I don't know my way around KDE at all - I don't know where the system volume is, don't know which driver it's using, I don't know anything about what's going on with the sound.

EDIT: Apparently, it's using the XINE engine.

---

### Post by sandyd on 2009-02-25
nvm......

---

### Post by Unanimated on 2009-02-25
bump

---

### Post by Unanimated on 2009-02-26
I just upgraded to 8.10, still with no sound.

---

### Post by HavocXphere on 2009-02-26
Here is what I did when I lost sound in kde4...maybe its of use:
[http://ubuntuforums.org/showpost.php?p=6762758&postcount=5](http://ubuntuforums.org/showpost.php?p=6762758&postcount=5)

---

### Post by OffAxis on 2009-02-26
my sound went AWOL on me when I upgraded to 8.10 (it started coming out of my onboard audio instead of my SoundBlaster Live card even though my SB card was topping the list in audio preferences).
When I upgraded to kde 4.2 I lost sound on both. Switching to gstreamer as the preferred engine would crash the audio. The 'test' button only worked for PCM audio. xine itself wouldn't output any sound.
Some people have fixed their sound issues by removing the gstreamer phonon package

```
sudo apt-get remove phonon-backend-gstreamer
```

This didn't work for me. I had no audio at all after removing that package (libxine1-plugins was also auto-removed at this time, I think). So no audio in the Preferences--> Test button, no audio in xine (the only remaining 'engine'), no system sounds.

After re-install of that removed gstreamer package, everything worked! Even xine, which I find odd. Maybe a dependency was missed in the original pacakge? I don't know. ( xine is still listed as my preferred engine)
```
sudo apt-get install phonon-backend-gstreamer
```

---

### Post by Unanimated on 2009-02-26
Okay, I installed gstreamer, xine-plugins, changed the master channel, added Audigy Digital Output Jack and muted it (that's how it was in Ubuntu), and plugged the speakers into the right port on the card. Now the sound works =D

---

