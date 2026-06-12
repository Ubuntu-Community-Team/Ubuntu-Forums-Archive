---
title: "No sound on my Asus A7U"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by oliilo1 on 2009-06-17
I installed my first edition of Ubuntu for some hours ago, and I really enjoy it, however the sound does not work.

I've tried to google abit around to figure it out, but it seems that the instructions are a bit to advanced for me still...

I've tried to follow: [http://ubuntuforums.org/showthread.php?t=846145](http://ubuntuforums.org/showthread.php?t=846145) but without any luck, I'm afraid :(



Thanks in advance ;-)

---

### Post by oliilo1 on 2009-06-17
I can also add that I have checked alsamixer, everything is on.
I've got alsa 1.0.20 drivers.

(however, when I open /etc/modprobe.d/alsa-base, and etc/modprobe.conf they was empty before I put in the "options snd-hda-intel model=lenovo", is this normal?.
also, Ive tried diffrent models, lenovo, realtek, auto, none wich seem to work.)

also, when I unmute "Front Mic" I hear misterious clicking sounds everytime I click with my keyboard mouse, from my headset, even if its connected in the headset plug...

---

### Post by oliilo1 on 2009-06-18
Nobody? :(

---

### Post by oliilo1 on 2009-06-18
So, a little update, I've been experimenting with alsa, and ive actually managed to  install alsa-driver-1.0.20, alsa-libs-1.0.20, and alsa-utils-1.0.20. and ran through the alsaconfig, opened alsamixer, put everything to high/on there.
but, there is still no sounds, although I hear weird clicking noices when I put on a normal song on youtube. so I decided to play a bass test, and I could hear a very deep bass, wich would mean there are atleast some connections, I would think.

(and before anyone asks, yes PCM is unmuted and on full volume)

---

