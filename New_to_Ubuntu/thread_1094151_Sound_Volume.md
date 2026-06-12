---
title: "Sound Volume"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by hashashi on 2009-03-12
Hi everyone, 
My sound card works perfectly but i get half or less the volume i get on windows. Which configuration should i be using?
I also had similar issues on windows actually. This volume grade thing is related to sound codecs as far as i know, because also on windows i always got double much volume on gom player as i get on bs player, because they simply use other audio codecs.
Any suggestions about audio codecs or movie players would be very useful,
Thank you
(Ubuntu 8.10, i don`t know what brand my sound card is, but it had no problems with running)

---

### Post by Eisenwinter on 2009-03-12
Have you checked the ALSA Mixer?
Open terminal:
```
alsamixer
```

You can adjust volumes and tones (such as bass) in there. Press ESC to quit the application.

---

### Post by hashashi on 2009-03-12
It was no good, everything is set to 100 on Alsamixer. I discovered that OSS slightly increases the volume level, but it ain't enough neither. 
Any other information could be really useful. 
Thank you

---

