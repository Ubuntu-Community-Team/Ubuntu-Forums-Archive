---
title: "changing sound at login causing problems"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by kvs on 2009-05-29
hey, i wanted to change the sound that ubuntu plays at login, just for fun. i converted the mp3 file i wanted to play into a .wav file, and then trimmed it using audacious to about 3 seconds. i went to system->administration->login window and changed the file in there. when i rebooted, it worked fine, played the file at login, however, after logging in, i couldnt play any file in any sound player. i increased the volume to fill, yet it wouldnt play any file. after that, i restored default settings in the system->administration->login window, and rebooted again, it played the default sound, and i was able to open sound files after that. why is this thing happening. why cant i play any files after changing the login sound?

---

### Post by durand on 2009-06-04
I think there is a bug with the way the sound server is started. Maybe file a bug report at launchpad.net.

---

