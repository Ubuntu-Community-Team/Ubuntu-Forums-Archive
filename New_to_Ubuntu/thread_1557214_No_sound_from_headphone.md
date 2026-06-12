---
title: "No sound from headphone"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by wenkey27 on 2010-08-20
I have installed Ubuntu 10.04 alongside Windows 7 in my Dell Studio 1558 notebook. Audio works perfectly with the built-in speakers of the notebook. There is no audio output when I connect a headphone to the jack.

Please help me to resolve this.

Thanks in advance.

---

### Post by Shpongle on 2010-08-20
taken from here [http://ubuntuforums.org/showthread.php?t=1469949](http://ubuntuforums.org/showthread.php?t=1469949)


See here: [http://ubuntuforums.org/showpost.php...85&postcount=3](http://ubuntuforums.org/showpost.php...85&postcount=3) and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). In short, put "options snd-hda-intel model=dell-eq" into "/etc/modprobe.d/alsa-base.conf".

---

### Post by wenkey27 on 2010-08-20
Thank you so much. This worked fine.

---

