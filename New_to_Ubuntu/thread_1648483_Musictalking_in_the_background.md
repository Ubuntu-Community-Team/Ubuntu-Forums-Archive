---
title: "Music/talking in the background"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by onename1 on 2010-12-18
I have installed UBUNTU on a SONY VAIO PCV-RS720G.  Which has a tuner card in it which was connected to cable tv when I installed it.  Whenever I log into UBUNTU  I have a music/talking in the background.  I discovered that is coming form the tv tuner (for when I unplug the cable tv it was static).  My question is:  What program is running that is receiving the signal? And how do I turn it off?  

I opened up 'system monitor' and could not figure out what program it was.  Any suggestion?

Thank you!

---

### Post by cariboo on 2010-12-19
You probably have your tv tuner card set as your main sound device. Right click the audio icon in the upper panel and select  Sound Preferences, Click the hardware tab and select your internal sound device instead of the tv tuner card.

---

### Post by onename1 on 2010-12-20
Thank you - cariboo907 - for you advice.  I followed the steps but only one card appeared in the hardware section.  When I turned off that card it turns off sound output from rhythmbox (& other apps) but the sound from the tuner card still is coming through.  Any further suggestions? (when I click on the mute button on the audio icon the sound form the tuner card does mute).  thank you.

---

### Post by sandyd on 2010-12-20
> **onename1 said:**
> Thank you - cariboo907 - for you advice.  I followed the steps but only one card appeared in the hardware section.  When I turned off that card it turns off sound output from rhythmbox (& other apps) but the sound from the tuner card still is coming through.  Any further suggestions? (when I click on the mute button on the audio icon the sound form the tuner card does mute).  thank you.
open a terminal (applications -> accessories -> terminal)
type in
```

alsamixer
```
mute the line in, microphone outputs, and then play with the settings until the static disappears.

---

### Post by onename1 on 2010-12-21
Thank you sandyd!  After experimenting for about 10min I discovered that when I hit mute CD that got rid of the 'noise' coming from the tuner.  Thank you again.

---

