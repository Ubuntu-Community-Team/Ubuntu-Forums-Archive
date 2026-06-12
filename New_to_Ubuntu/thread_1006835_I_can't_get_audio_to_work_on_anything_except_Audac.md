---
title: "I can't get audio to work on anything except Audacity."
date: 2008-12-09
forum: New to Ubuntu
---

### Post by littlejimmystyle on 2008-12-09
I'm getting really confused by the sound settings.
I'm using a SoundBlaster Live 24 usb sound card and I can't get anything to play except audacity, which is recording and playing quite happily. I've set everything I can find to the right sound card and tried all kinds of things I've found. 
I've set up JACK to use my soundcard and it says it's runing and still nothing happens.
Any ideas would be greatly appreciated because I'm going a little bit mad.

---

### Post by redseventyseven on 2008-12-09
Does the sound not work for other programs regardless of whether or not Audacity is running? (i.e. close Audacity completely and try running another program that wasn't working before)

---

### Post by littlejimmystyle on 2008-12-10
No.
I managed to get last.fm working by setting it use to my usb soundcard in the audio my settings. But I can't find anywhere on Firefox or Ardour (Which is what I mainly want to use) that lets me set them to use that soundcard.

---

### Post by markbuntu on 2008-12-10
If audacity is running, it will not let any application use the sound device. If jack is running ardour should run with no problem if audacity is not. Just be sure to have jack running before starting ardour.

If you really want to get Firefox and ther apps that use pulsaudio to go through jack, you can use this guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Just remember, audacity will mess up everything whenever it is running.

---

### Post by littlejimmystyle on 2008-12-10
Ardour doesn't work when I start jack, even though jack says it's working and it's set to my sound card. 
And I'm not running audacity at the same time, I was just saying that to show that my system is recognising the soundcard.

---

### Post by markbuntu on 2008-12-11
The order of your sound cards can change at every reboot so make sure that whatever hw: you set jack to use really is your sb card.

---

