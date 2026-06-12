---
title: "Totem"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by hifly1231 on 2009-06-04
I recently purchased a Logitech Clear Chat USB Wireless Headset.  I have my Skype set for Audio In & Audio Out to run through my headset, and for Ringing to run through my speakers.  Working great.  I also figured out how to switch Amarok from speakers to headset and back.  Also working great. However, I'm having a problem with Totem.  It keeps switching to the audio running through my headset on it's own, and that's not what I want.  How do I switch Totem back to playing through my speakers, and make it stay that way without uninstalling Totem, unplugging my USB Headset, and reinstalling Totem, which is what I did the last time?

---

### Post by mcduck on 2009-06-04
You could try installing PulseAudio Volume Control (the package is called "pavucontrol"). It allows controlling volume and output device individually for each application.

---

### Post by hifly1231 on 2009-06-04
> **mcduck said:**
> You could try installing PulseAudio Volume Control (the package is called "pavucontrol"). It allows controlling volume and output device individually for each application.

OK, I've installed PulseAudio Manager, so now how to I configure Totem from inside of there for speaker output instead of headset output?  Or is there an even easier way than PulseAudio Manager?

---

### Post by mcduck on 2009-06-04
> **hifly1231 said:**
> OK, I've installed PulseAudio Manager, so now how to I configure Totem from inside of there for speaker output instead of headset output?  Or is there an even easier way than PulseAudio Manager?

You want PulseAudio Volume Control (which is what I suggested for you), not PulseAudio Manager..

Just open the volume control, and on Playback-tab oyu'll see separate entry for each of your running program that outputs audio. There's a slider for adjusting volume, mute & lock buttons and next to them a dropdown which allows you to select the device to use for that program's output.

---

