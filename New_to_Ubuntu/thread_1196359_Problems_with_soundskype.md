---
title: "Problems with sound/skype"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by bubbhasdance on 2009-06-24
My Skype (2.0.72) works perfectly, I can use my webcam and sound works great. The only time it doesn't work, is when I use my audio for anything. That includes youtube video, songs on Songbird, anything involving audio, Skype gives me the "Problems with Audio Playback" notice whenever I call someone.

Restarting the computer fixes this problem, but only until I use audio again. Is there any way that this can be fixed? I'm very tired of having to restart the computer every time I want to use Skype.

Thanks in advance.

---

### Post by fugaki on 2009-06-24
I have this same problem, but to fix, I just quit out of any other application tht could be loking the sound device and restart Skype. Works everytime for me.

---

### Post by RedRat on 2009-06-24
Are you using the ALSA or Pulse Audio system? Try the Pulse Audio under sounds: Preferences>Sound

Under Devices, select PulseAudio Sound Server. Try that.

---

### Post by bubbhasdance on 2009-06-24
This worked perfectly, thanks. I didn't even have to restart Skype, which is a plus. I will also try out the second post, maybe I won't have to close the program with this one. I'll let you know.

---

### Post by bubbhasdance on 2009-06-24
> **RedRat said:**
> Are you using the ALSA or Pulse Audio system? Try the Pulse Audio under sounds: Preferences>Sound

Under Devices, select PulseAudio Sound Server. Try that.
Running both ALSA and Pulse Audio, I believe. I only use Alsa for switching the sound from headphones to speakers using the alsamixer command. Pulse Audio controls my speakers and most of my audio inputs, if not all.

I couldn't find the dialog box that you referred to, as well. :(

---

