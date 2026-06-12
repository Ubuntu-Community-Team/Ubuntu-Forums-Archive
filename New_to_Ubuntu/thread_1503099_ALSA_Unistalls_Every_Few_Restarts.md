---
title: "ALSA Unistalls Every Few Restarts"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by linuxwolverine on 2010-06-06
I have a Sony Vaio F series running 64-bit 10.04.  Ever since the last kernel update about every three restarts my sound card disappears leaving only a 'dummy output' under the output tab.  I can reinstall ALSA 1.0.23 and the sound works on reboot, but will disappear when shutdown once or twice.

I am pretty new to this so I am not sure what information you need, but let me know and thanks for the help.

I ran 

cat /proc/asound/card0/codec#* | grep Codec 

Which told me my sound card was

Realtek ALC275

---

