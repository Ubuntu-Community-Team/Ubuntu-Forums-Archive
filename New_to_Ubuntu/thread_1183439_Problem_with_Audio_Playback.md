---
title: "Problem with Audio Playback"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by SKYDOS on 2009-06-10
i want to call someone in skype, but i have this problem [http://ipicture.ru/Gallery/Viewfull/19750897.html](http://ipicture.ru/Gallery/Viewfull/19750897.html)

what i need to do to remove this error?

thanks!

---

### Post by dileepm on 2009-06-10
Does your Ubuntu box plays other audio stuff

---

### Post by Baelus on 2009-06-10
Try closing any other app that may be using the audio out (like vlc ;)).

Then give it a try.

---

### Post by dileepm on 2009-06-10
Make sure you have gstreamer plugins installed

---

### Post by gradinaruvasile on 2009-06-10
That error could have multiple causes. I see you are running vlc. Stop any applications that uses sound playback and try again.
Also what audio output are you using - ALSA or Pulseaudio? You must select the corresponding one in the audio devices tab in Skype.

---

