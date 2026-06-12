---
title: "very very low volume"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by sohini on 2010-04-06
hi,
i am only two-day user of ubuntu. My friend helped me install ubuntu in my Dell inspiron 1440 laptop laptop last night.
Everything is working fine except the sound. Video is playing but I can't hear anything in speaker. in headphone, the volume is too low to hear.

Can anyone please suggest how to fix this problem? I am not very comfortable with using the terminal by writing code as i am using it for two days only. please suggest some solutions.

---

### Post by NightwishFan on 2010-04-06
You will like this terminal command, it is as graphical as they come. Open the terminal using Applications -> Accessories -> Terminal, type this, and push enter.
```
alsamixer -c0
```

You can make the mixers louder using the arrow keys, press esc to exit.

---

### Post by sohini on 2010-04-06
thanks for your suggestion. i did that. but unfortunately still the same problem. however i heard a beep as i was typing wrong key in the terminal. is there any other problem?

---

### Post by sohini on 2010-04-06
should i change anything in System>Preferences>Sound? in the sound playback or the device?

---

### Post by NightwishFan on 2010-04-06
No the beep would not do anything. So the mixers did not help your volume problem? If you hear sound at all the above command should enable you to get the correct sound levels. Were they all at full?

Also, check the sound applet next to the clock, right click it and hit Sound Preferences. See if your output is muted.

As for System -> Preferences -> Sound leave everything as the default. Do you know what version Ubuntu you are running?

---

### Post by sohini on 2010-04-06
both the master and output volume is 100% in top panel (next to the clock).
in the mixer all volumes were 100%.

i have set all of the device to autodetect mode in sound preferece. what would be the device? there is no autodetect or default option.

the version is 9.04 (Jaunty).

---

### Post by ibuclaw on 2010-04-06
You could try [http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

Which comes with a preamp (probably best not to set it above 1.5x, as I can imagine that sound will just become distorted).

---

### Post by lidex on 2010-04-06
Right-click on the alsa-info script link in my sig and download to your user folder.
Open a terminal: "Applications>Accessories>Terminal"
and enter this command:
```
sudo bash utils_alsa-info.sh
```

Post the results here using code tags or provide a link if you choose to upload.

---

### Post by sohini on 2010-04-09
but it cannot be saved...

i have now installed ubuntu 9.10. i heard that there is sometimes some sound problem in 9.04.

but in 9.10, the headphone is working, not the speaker.

can there be some problem like it is not supporting the speakers?

---

### Post by lidex on 2010-04-09
Actually there are more audio issues in karmic out of the box. Work through this thread:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

And make sure your levels are up/unmuted in alsamixer, including PCM.

---

