---
title: "How do I reinstall sound card drivers?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by gshockxc on 2009-07-29
My sound isn't working and I'd like to try reinstalling the sound card drivers.  Can someone help me?  

Do I need to use Synaptec?  Adept?  I think they were automatically recognized on install.  Thanks.

---

### Post by llamabr on 2009-07-29
This is unlikely to be a drivers issue.  What did you change so that now they're not working?

---

### Post by gshockxc on 2009-07-30
> **llamabr said:**
> This is unlikely to be a drivers issue.  What did you change so that now they're not working?

I installed some updates, from the Update Notifier in the panel.  

Here's what was installed when it stopped working.

Commit Log for Mon Jul 20 17:14:07 2009

Installed the following packages:
gstreamer0.10-pulseaudio (0.10.14-1ubuntu0.1)
libpulse-browse0 (1:0.9.14-0ubuntu20.2)
libpulsecore9 (1:0.9.14-0ubuntu20.2)
libspeexdsp1 (1.2~rc1-1)
pulseaudio (1:0.9.14-0ubuntu20.2)
pulseaudio-esound-compat (1:0.9.14-0ubuntu20.2)
pulseaudio-module-hal (1:0.9.14-0ubuntu20.2)
pulseaudio-module-x11 (1:0.9.14-0ubuntu20.2)
pulseaudio-utils (1:0.9.14-0ubuntu20.2)

Thanks.

---

### Post by albanodesign on 2009-07-30
have you waited until the update finishes?
dont play audio when it is updating 
try it again and restart computer after updete finishes

---

### Post by gshockxc on 2009-07-30
> **albanodesign said:**
> have you waited until the update finishes?
dont play audio when it is updating 
try it again and restart computer after updete finishes

I didn't use the audio until the next day.  I shut down my machine sometime after the updates finished, and restarted the next morning.  Those updates were installed on July 20th, 2009.  I've shutdown and restarted every day since then.  Still no sound.

---

### Post by albanodesign on 2009-08-01
try downgrading the pulseaudio

$ sudo apt-get downgrade pulseaudio

---

### Post by gshockxc on 2009-08-02
No luck.

```
E: Invalid operation downgrade
```

I just realized this weekend that I overlooked the fact that I'm running 64-bit Jaunty.  I neglected to mention that, and I don't know if it's part of the reason I'm having issues.  Will check that in the x86-64-bit forum.

---

