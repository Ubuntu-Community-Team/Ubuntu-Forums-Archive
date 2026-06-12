---
title: "Very annoying video issue"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by samh785 on 2009-10-05
Two days ago I upgraded to 9.10. I had installed all of the restricted formats, and all seemed to be well and good until I tried to install the OpenShot video editor. This destroyed my ability to watch videos on VLC and Totem. I fixed the issue with being able to watch videos and such, but it has given rise to a more discreet, and yet just as annoying issue. When I start up my computer, all videos play absolutely fine. Then for no apparent reason, after about an hour or so when I'll try to play them again. The video works fine, but the audio will have become very skippy and rendering the video impossible to watch with out raging. I am not 100% sure if this has to do with a specific program messing with the codecs, but I have tried to isolate a specific one, and I have yet to find any that allow me to recreate the annoying effect just after starting the computer. 

Please help me, this is really really annoying.

[RIGHT]Regards,
Sam
:popcorn:
[/RIGHT]

---

### Post by lavinog on 2009-10-05
What video card are you using, and did you enable any restricted drivers?

How did you upgrade to 9.10?

Do the videos in the examples folder experience these issues?

---

### Post by samh785 on 2009-10-05
my video card is an Nvidia GeForce 8600 GT. Yes I have enabled the restricted drivers, and no the videos in the examples folder do not experience this issue.

---

### Post by samh785 on 2009-10-05
Scratch what I said earlier about it being totem and VLC, it's only VLC. That sucks too, because VLC is what I prefer to use...

---

### Post by lavinog on 2009-10-05
I don't have alot of experience with nvidia, but it could be the settings in vlc:
startup vlc, goto tools>preferences>video. What is output set to? Does switching between xvideo, x11 and opengl.
also if you turn on advanced settings (bottom left) then go to video>filters, make sure you don't have any filters enabled.

---

### Post by samh785 on 2009-10-05
I have found a bug listing dealing with this issue: [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/402018](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/402018)

The suggestion on the bug listing was to set the audio to pulseaudio specifically, and not default. So far it seems to be working on my machine, and I'll post again if it changes.

---

