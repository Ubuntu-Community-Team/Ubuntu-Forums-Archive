---
title: "Flash Player Audio Problem."
date: 2009-01-22
forum: New to Ubuntu
---

### Post by CommBreakdown on 2009-01-22
I've been running Ubuntu 8.10 for a couple of weeks now and just a couple of days ago encountered a problem with Adobe Flash Player 10. I run all my audio on my laptop through a USB DAC but when I use Adobe Flash Player (to play a YouTube clip for example) it uses my laptop internal speakers instead of my external speakers or headphones. How can I rectify this problem?

Thanks in advance.

---

### Post by cyberfin on 2009-01-22
I suggest you take a look on your sound settings in Settings>Preferences>Sound and change the pop-down menus to your sound card from auto. If it doesn't work you can always change back.

I don't know if it will have anything to do with it but sometimes when I have problems with flashaudio (not always) I have to kill pulseaudio: in terminal write "killall pulseadio" and try (if 1st solution doesn't work)

Hope it helps.

---

### Post by CommBreakdown on 2009-01-22
That didn't work..

---

### Post by markbuntu on 2009-01-22
There are a few things that can be causing this problem. The most likely is that flash is defaulted to the wrong device by pulseaudio. If that is the case you can fix it easily by opening the pulse audio volume control and when a flash is playing right click on the stream and choose move stream and move it to the usb device.

If flash does not show up in the pulseaudio volume control go to system/preferences/sound and change the Music and Movies/SOund Playback to Pulse Audio Sound Server.

If you do not have the pulse audio volume control in Applications/Sound and Video, you are most likely missing a bunch of other important stuff and your sound configuration is not optimized. Go here for that

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by CommBreakdown on 2009-01-23
Thank You! Installing those packages fixed the problem, I had to reboot my computer to get PulseAudio to start working though.

---

