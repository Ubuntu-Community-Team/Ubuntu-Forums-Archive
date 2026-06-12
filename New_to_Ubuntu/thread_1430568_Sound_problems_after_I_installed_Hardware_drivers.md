---
title: "Sound problems after I installed Hardware drivers"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by Djalmahal on 2010-03-15
Hi,

on my old Toshiba Laptop I installed a propitiatory driver for the Modem (screenshot attached), the description mentions ALSA, after this the sound crackles and is very bad, uninstalling the driver didn't restore the sound to it's previous state. How can I force Ubuntu to reconfigure it's audio?
I checked "sound preferences" and it's seems normal.

Thanks
Andreas

---

### Post by Djalmahal on 2010-03-15
Under soundpreferences>Hardware it list Internal Audio Analog Stereo Duplex (which should be correct) under Output it lists Internal AUdio Analog Stereo.

Under Multimedia System Selector>Audio it list for Output ALSA and Device Default, which should do the trick. 

So, how can I go back to the Original configuration, is there a backup file or a command that forces to reconfigure?
 At last an atachment for the command alsamixer.

Thanks for your help
Andreas

---

