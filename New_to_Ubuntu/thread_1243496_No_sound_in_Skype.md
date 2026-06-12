---
title: "No sound? in Skype"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by jacklinux on 2009-08-18
i recently got a USB connected headset, and it plays sound via everything apart from Skype. My mic is fine, but there is not sound from Skype in a call.
Does anyone know why?
Fixed that problem, now i can't turn skype down even when using the headset volume, or the Ubuntu volume controls.

---

### Post by chuuk on 2009-08-18
Open up your system monitor, find 'pulseaudio' in the list of running processes and kill it (right click, select Kill). pulseaudio and Skype do not work well.

Should solve all your problems.

---

### Post by JoshStrobl on 2009-08-18
I'd go into System>Preferences>Sound and...
1. Make sure Sound Capture is USB Device 
2. When it Skype call change Sound Playback in Audio Conference to AutoDetect
3. Go to Skype> Options then do a Test Call
0_0 Work?

---

### Post by jacklinux on 2009-08-18
Nope, the sound still won't change.

---

