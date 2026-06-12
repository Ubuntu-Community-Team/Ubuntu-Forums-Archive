---
title: "Where do I start?"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by chickengeorge on 2009-02-02
I have decided to bite the bullet and completely wipe my harddrive and run ubuntu 8.10

Everything has worked fine apart from the sound which I can't seem to get to work. I have found a few guides but everything seems way too complicated.

I'm running Ubuntu 8.10 on a Sony Vaio VGN-FZ21M

I have managed to find out that my audio chipset is Intel Corporation 82801H (ICH8 Family)

Is there anybody who can tell me exactly what to do to get my sound working?

Regards from a Linux noob :)

---

### Post by jbrown96 on 2009-02-02
I have the exact same audio chipset, but in a Thinkpad. I've never had any problems, but I can try to help.

Pulseaudio is a new sound server that supposed to be great and have tons of features, but I think it's really, really bad. Lots of people seem to be having problems, so my general recommendation is to switch back to ALSA, which is a much more stable sound server. It should be an easy switch.

1) Open a terminal. Applications--->Accessories--->Terminal
2) check and see which sound server you are using. ```
alsamixer
```
If there's only one channel, then it's pulseaudio. If this is muted or turned down, try turning it up with the arrow keys. 
3) Exit alsamixer by pressing the escape key. Don't quit the terminal.
4) Switch to ALSA. System--->Preferences--->Sound. Switch everything to ALSA. Don't exit this window.
5) Go back to the terminal and use alsamixer again. There should be a lot more channels available (if not try a reboot). Turn the master down to around 80, so it's not too loud. 
6) Back in the sound dialog, "test" the sound playback. It's just a constant tone. If you can hear this, great. If not post back with what happened. 

Tweaks:
You will probably want to be able to use the volume slider near the clock or your volume hardware keys. We need to make sure that the correct channel is being controlled by them. Go back into alsamixer and try your hardware keys or the volume slider. The master channel should move up and down, if not you need to change the selected channel. Right click on the volume slider and choose preferences, then select master. PCM and Front sometimes affect voluem, so they should be turned up all the way. The other channels should generally be muted, because they can cause feedback (static), so unless they are needed (i.e. microphone or headphone channels), mute them.

---

### Post by chickengeorge on 2009-02-02
Thanks for your help but when I try that command it tells me that there are no mixer elems found. I'm not sure what this means.
```

chicken@chicken-laptop:~$ alsamixer
No mixer elems found

```

Regards,

ChickenGeorge

---

### Post by jbrown96 on 2009-02-02
What happens if you go into the sound dialog and try to test sound playback?

---

### Post by chickengeorge on 2009-02-02
I get an error alert saying

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample !
gconfaudiosink: Failed to connect stream:
Invalid argument

Thanks

---

