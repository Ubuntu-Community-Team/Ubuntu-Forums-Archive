---
title: "Mic not working - Jaunty"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by Fifthmarch on 2009-11-22
My microphone does not work - either with sound recorder or Skype. I have a ALC888 sound card, and I have tried updating the driver, but it still doesn't work, though I can hear the sound through the headphones. The sound card is fine, and my technician says its probably a problem with the mixer settings. I have tried reinstalling Skype. Can anyone suggest a solution? I'm running 9.04 Jaunty. Will upgrading to Karmic solve the problem?

Thanks

---

### Post by Sealbhach on 2009-11-22
> **Fifthmarch said:**
> My microphone does not work - either with sound recorder or Skype. I have a ALC888 sound card, and I have tried updating the driver, but it still doesn't work, though I can hear the sound through the headphones. The sound card is fine, and my technician says its probably a problem with the mixer settings. I have tried reinstalling Skype. Can anyone suggest a solution? I'm running 9.04 Jaunty. Will upgrading to Karmic solve the problem?

Thanks

I had trouble with Skype but I found that when I installed aumix and fiddled with the volume controls I got it working OK.

.

---

### Post by laidback on 2009-11-22
Have a look here:-

Top right of screen you'll find a loudspeaker icon on the task bar. Press it, then you'll see "Volume Control.." press that too. Now you'll see a window called Volume Control that works rather like Alsa Mixer. Adjust controls as required. If a control isn't visible goto Preferences and activate it. Notice also that on the first screen you can select the "Device" to adjust, choose as required. I found it worked for me when I had problems with the mic apparently not working when all else did.

---

### Post by Fifthmarch on 2009-11-22
Thanks, I've tried adjusting the controls, but the microphone is always muted in HDA Intel (Alsa Mixer). I tried clicking to unmute it, but it gets muted again as soon as I close the  control window.

---

### Post by Fifthmarch on 2010-07-29
Thanks for the help. I tried everything mentioned here, but the only thing that works is to delete pulseaudio completely, install the latest version of alsaplayer and then use alsamixer to edit the sound controls. After that, play around with the Skype audio controls to pick the right set of options. 

I had the same problem in Karmic, and when I tried out Lucid using the Live CD.

---

