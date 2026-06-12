---
title: "Skype"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by rocker-billy on 2011-04-06
Have got Skype up and running but when i go to the options and select 'sound devices' the following appears:

It appears your system has Pulse Audio running: to change sound settings you need to use your desktop manager volume control or PulseAudio volume control?

I know this is a stupid noob question but could someone help me out here please.

---

### Post by khelben1979 on 2011-04-06
The latest versions of Skype for Linux does not require [Pulse Audio]("http://en.wikipedia.org/wiki/Pulse_audio") to work if you're struggling with getting a microphone working or similiar. Just configure Skype to use the [ALSA]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture") system instead as sound system if your Ubuntu system allows you to do that. If not, uninstall Pulse Audio could be a solution to your problem.

*One advice: if uncertain, don't do things which can damage the system and use the man pages to read to check things up so you know what you're doing.*

---

### Post by mikewhatever on 2011-04-06
So what is the question exactly?

---

### Post by rosencrantz on 2011-04-06
You don't *need* to use pulseaudio, but it doesn't do a bad job with skype. 
Get the pavucontrol GUI
$ sudo apt-get install pavucontrol 
to control your audio streams for skype. (I use it all the time because my microphone seems to get muted every time I hibernate)
If you aren't familiar with Alsa configuration, it's probably easier than uninstalling pulseaudio.

---

### Post by rocker-billy on 2011-04-06
Ok, this is what i did.
1) I opened a terminal and typed: sudo apt-get remove PulseAudio
2) I then went to System => Preferences => Sound
3) Select the Hardware tab and i selected my webcam (in my case QuickCam Sphere)
4) Now click on the Input tab and this time i selected QuickCam Sphere Analog Mono
5) close

When i opened up Skype and went to Options => Sound Devices click on Make a test call and that's it.

I can now make a successful test call. It worked for me although the sound quality is not the best.

---

### Post by khelben1979 on 2011-04-06
Sounds good!

---

