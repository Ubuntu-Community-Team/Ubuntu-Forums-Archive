---
title: "ALSA problem"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by ojones117 on 2009-07-08
Hi everyone,

Pretty new to Ubuntu, I've been doing fine for the past two weeks (new install of 9.04) and yesterday I ran into a problem. After applying all recommended updates and buggering around with a hard drive mount point (which the drive refused to mount but I managed to force it in the end). My sound stops working!

In sound preferences, everything was set to "Autodetect" and when I pressed "test" the testing window would open but no sound. If I set it too "HDA Intel AD198x Digital (ALSA)" the same problem occurs. If I set it too "HD Intel AD198x Analog (ALSA)" and hit test, I get this: 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

I am able to get a test tone from "HDA Intel AD198x Analog (OSS)" but that appears to only allow me to use one application at a time. For instance I have to close Rythym box completely before watching a video (the audio component) on VLC will work. 

I think I should also point out that when everything is set to the Digital ALSA option, and NO sound what so ever is working (tried many applications), when I log in, I get the log in successful sound.

Let me know if I've left out any relevent information and thanks for the help in advance.

---

### Post by ojones117 on 2009-07-08
I hate to bump, but I'm really struggling with this problem and would appreciate any advice anyone has.

---

