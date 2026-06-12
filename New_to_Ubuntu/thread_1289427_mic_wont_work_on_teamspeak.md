---
title: "mic wont work on teamspeak"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by eMan520 on 2009-10-12
Hi I can't seem to get my mic to work on teamspeak 2. Im runnign ubuntu 8.10. my mic works because i recorded my voice in audacity
My computer is an hp pavilion 540n

---

### Post by DrDevice on 2009-10-12
Currently Teamspeak uses OSS for sound, and has a nasty habit of wanting to take exclusive control of your soundcard input/output.  I use a wrapper to make it work a little more nicely, might bring your microphone into line.

Press Alt+F2 and try this:```
aoss teamspeak
``` for normal alsa, or if you have Pulseaudio installed try ```
padsp teamspeak
```  You may need to install alsa-oss from the repositories.  Hope that works for ya.

---

