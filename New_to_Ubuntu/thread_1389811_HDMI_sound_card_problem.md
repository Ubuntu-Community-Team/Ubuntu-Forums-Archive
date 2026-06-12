---
title: "HDMI sound card problem"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by Archer Troy on 2010-01-24
I recently received the Auzentech X-Fi Hometheater HD soundcard for my HTPC. It has HDMI output. However, the HDMI doesn't transmit audio to the tv like its supposed to. I'm pretty new to Ubuntu and don't really know what do at this point.

Any help would be appreciated.

---

### Post by Greenwidth on 2010-01-24
If you right click the sound icon and select preferences > Hardware tab is HDMI (Digital) out listed under profiles?

---

### Post by Archer Troy on 2010-01-25
I dont have that option. I'm using mythbuntu and it comes with the mixer-plugin. where would I go to check this?

---

### Post by Greenwidth on 2010-01-26
```
xfce4-mixer
```
Should bring up the mixer, switch to HDMI, you might have add the controls (bottom left)

---

### Post by Archer Troy on 2010-01-29
thanks for taking the time to respond. It doesnt have the hdmi option. all I see are volume, PCM, and microphone.

---

### Post by Greenwidth on 2010-01-30
I think you might be out of luck with this card..
[http://www.linuxquestions.org/questions/linux-hardware-18/no-audio-with-auzentech-x-fi-forte-722560/](http://www.linuxquestions.org/questions/linux-hardware-18/no-audio-with-auzentech-x-fi-forte-722560/)

Auzentech support:
"As for other Auzentech soundcards, Linux drivers are not planned as of this writing (February 2009), because the main advantages of the soundcards are not available under that operating system."
[http://www.auzentech.com/site/support/FAQ.php](http://www.auzentech.com/site/support/FAQ.php)

:(

---

### Post by Archer Troy on 2010-02-07
That's what I was afraid of....That sucks!

Guess Windows and Mediaportal it is.... :(:(:(

---

