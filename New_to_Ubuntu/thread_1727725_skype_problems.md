---
title: "skype problems"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by panther10 on 2011-04-12
hello out there.
 I am at a loss. using ubuntu 10.4 with a logitec 9000 webcam. seems that everything works great on skype till someone calls me. then the video shuts down. i can see them but they can't see me.  plus the sound can be choppy as well. i tweak gstreamer and everything else imaginable but to no avail. posted this question a half dozen times and no response so far. anyone else have this prob or does anyone know what to do??  thanks for the help.. :D

---

### Post by rosencrantz on 2011-04-12
Hi panther10,
apparently no one has had your problem up to now. Skype can be pretty erratic.
According to the UVC wiki, the webcam is supported. ([http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/))
Does the test preview in Options->Video devices work?
Do you have sufficient bandwidth for video calls (this might explain the choppy audio)? If in doubt, try speedtest.net
What Skype version are you on?

---

### Post by cbspace on 2011-04-12
What rosencrantz suggested is pretty much what I would suggest.

I have the Logitech Pro 9000 Webcam and the only problem I had was PulseAudio has an annoying habit of selecting my onboard sound card on startup. However disabling the onboard sound card in the BIOS (since I never use it anyway) resolved that issue for me.

With my Skype + webcam the video and audio work smoothly, no fiddling around or tweaking necessary - sometimes I get connections issues, however a restart of skype sorts that out, as rosencrantz  said, it is erratic.

What version of Ubuntu and Skype are you using?

---

### Post by earthpigg on 2011-04-12
> **cbspace said:**
> What version of Ubuntu and Skype are you using?

I'm sure he is using the same version of skype that we all are: the beta version from 2008 iirc.

---

### Post by cbspace on 2011-04-12
> **earthpigg said:**
> I'm sure he is using the same version of skype that we all are: the beta version from 2008 iirc.

More than likely - stupid question on my part. Skype need a kick up the backside!

---

### Post by earthpigg on 2011-04-13
> **cbspace said:**
> More than likely - stupid question on my part. Skype need a kick up the backside!

or we all need to boycott them and use stuff from folks that care about us.

---

