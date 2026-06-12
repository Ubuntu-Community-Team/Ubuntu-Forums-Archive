---
title: "Recording Audio output with Sound Recorder"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by mogsmar5 on 2009-05-07
Hi

I'm trying to set up Sound Recorder so that my brother (no computer person, hence why I'm not using Audacity) to record the Audio output of my computer. So far I haven't had any luck - all I record is static. I've googled around and found references to ALSA and MIX, though I don't know what these are or how to use them. Could someone help?

---

### Post by durand on 2009-05-07
Go to the volume control preferences and tick all the boxes. Then see if any of the sliders are mute or have a low volume.

---

### Post by mogsmar5 on 2009-05-07
Doesn't seem to work. And when I move up the slider on one called MUX the computer keeps making a static sound all the time.

---

### Post by durand on 2009-05-07
Hmm, another thing you could try to do is change the recording from Pulseaudio to Alsa in System > Preferences > Sound. That may do the trick..

---

### Post by mogsmar5 on 2009-05-07
How do you do that? There isn't a recording group - just Sound Events, Music and Movies and Audio Conferencing. None of them seems set to Pulse Audio though.

---

### Post by durand on 2009-05-07
They're not set to pulseaudio? That's quite strange. Sorry I can't help you much but I'm not on ubuntu at the moment so I'm just trying to help from memory. You could try paspender gnome-sound-recorder. Or whatever the command for sound recorder is. That will suspend pulseaudio while the application is running.

---

