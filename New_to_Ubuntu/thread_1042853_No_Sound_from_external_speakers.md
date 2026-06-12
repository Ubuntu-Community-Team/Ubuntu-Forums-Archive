---
title: "No Sound from external speakers"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by alienexplorers on 2009-01-18
Right now the only sound I get is the login sound and then nothing.  I can run mp3 or flash files and will have no sounds and when an error occurs I get no error sound.  I am running ALSA audio threw a SoundBlaster Live card.
Sound runs perfectly under Windows XP.

---

### Post by RomeReactor on 2009-01-18
Hi Alien. Have you tried switching everything to PulseAudio in 'System->Preferences->Sound'? Or, if you already have set PulseAudio there, stopping Pulse? (Close the applications first):
```
pkill pulseaudio
```
Then open them again and see if they work now.

Note: if you want to enable Pulse again:
```
/usr/bin/pulseaudio -D --log-target=syslog
```

---

### Post by alienexplorers on 2009-01-18
Works fine now thanks.

---

