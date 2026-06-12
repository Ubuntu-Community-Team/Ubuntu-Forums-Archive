---
title: "sound vanished"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by aussielinuxguy on 2011-03-09
Hi there,

I am using Ubuntu 10.04 LTS.

Yesterday i installed skype and plugged in my headset to see if it worked, and it did work. now i can`t play my mp3`s as i have lost my sound.

I checked sound preferences and no devices are muted.

Can someone help please ?

---

### Post by NightwishFan on 2011-03-09
Try unmuting them or rebooting.

---

### Post by aussielinuxguy on 2011-03-09
Nightwishfan, i did what you said, but still no sound.

---

### Post by NightwishFan on 2011-03-09
You don't have the headset in now? Also ensure you are using the correct device in the sound preferences. As a final option run this command:
```
alsamixer -c0
```

See if any mixers are muted or turned down that seem important. You can use space to unmute.

---

### Post by aussielinuxguy on 2011-03-09
No i removed the headset.

with my alsamixer v1.0.22, it shows

Master fr 0<>0

Headphone 100<>100

PCM 60<>60

Front 50<>50

Front Mic 0<>0

Line <>0

mic 0<>0

---

### Post by aussielinuxguy on 2011-03-10
Fixed my sound problem by reinstalling Ubuntu.

---

