---
title: "No sound in Mozilla/spotify"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Himym on 2009-06-07
Hey, I have configured Ubuntu to play Sound events,Music and Video and Audio conferencing in my headset. Although,there is no option on where to play music with softwares. Therefore,when  I watch a video or listen to music in mozilla or spotify, the music comes to my speakers instead. How can i configure softwares to play music through my headphones instead?

---

### Post by kostkon on 2009-06-07
Set your sound playbacks in your sound preferences (i.e. System &#8594; Preferences &#8594; Sound) back to *Autodetect*.

Then install the *PulseAudio Device Chooser* utility using *Synaptic*. This will allow you to set the default output device in your system, move the audio streams of your applications from your speakers to your headset on-the-fly and some other things.

For more info check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

Hope that helps.

---

### Post by heroidi on 2009-06-07
did you install ubuntu restricted extras?

---

