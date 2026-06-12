---
title: "snd cs46xx woes with pulseaudio machine gun noise bad sound"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by gigi1234 on 2010-01-16
I am running 9.10 on a Thinkpad T21 laptop. All I really want to do is to use this laptop to stream Internet radio and play it on a bluetooth speaker. There are two problems:

1) I installed Blueman and I can connect the speaker, no problem. But in preferences-> sound I don't see the device listed.

2) The sound card (cs46xx) doesn't seem to work with pulseaudio ([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619))

It makes a "machine gun" noise and sounds terrible. I have surmised that pulseaudio doesn't work with this soundcard. I tried uninstalling pulseaudio and installing esound, but that just broke the sound. 

Does anyone have a suggestion about what is going on and how to fix it?

Thanks!

---

### Post by sandyd on 2010-01-16
> **gigi1234 said:**
> I am running 9.10 on a Thinkpad T21 laptop. All I really want to do is to use this laptop to stream Internet radio and play it on a bluetooth speaker. There are two problems:

1) I installed Blueman and I can connect the speaker, no problem. But in preferences-> sound I don't see the device listed.

2) The sound card (cs46xx) doesn't seem to work with pulseaudio ([https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619))

It makes a "machine gun" noise and sounds terrible. I have surmised that pulseaudio doesn't work with this soundcard. I tried uninstalling pulseaudio and installing esound, but that just broke the sound. 

Does anyone have a suggestion about what is going on and how to fix it?

Thanks!
uninstalling pulseaudio should not break the sound
it should simply fall back to ALSA.

can you try and uninstall pulseaudio again (if youve uninstalled it) and do
```

sudo modprobe snd-cs4236

```
and pulseaudio problems are a mistery to everyone ATM. it works completely for some, and it doesn't work at all for some.

---

### Post by gigi1234 on 2010-01-16
Ok, I tried uninstalling pulseaudio again via:

sudo apt-get remove pulseaudio

then I rebooted and did the modprobe you suggested. and the sound is broken. when I go to preference-> sound it says "waiting for sound to respond" but it never does respond. 

Hmmm, not sure what else to try.

---

### Post by sandyd on 2010-01-16
what does 
```

sudo /etc/init.d/alsa* restart 
```give

---

### Post by gigi1234 on 2010-01-16
Hi, Thanks for helping me.

Nothing happens when I restart alsa as suggested. Everything is as it was before.

---

### Post by sandyd on 2010-01-16
whats the output of ```

aplay -l
```

---

### Post by gigi1234 on 2010-01-16
**** List of PLAYBACK Hardware Devices ****
card 0: CS46xx [Sound Fusion CS46xx], device 0: CS46xx [CS46xx]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 1: CS46xx - Rear [CS46xx - Rear]
  Subdevices: 31/31
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
card 0: CS46xx [Sound Fusion CS46xx], device 2: CS46xx - IEC958 [CS46xx - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by sandyd on 2010-01-16
everything actually seems to be okay on the driver side now...

check to see if any of your volume outputs is muted or set to low.

---

### Post by gigi1234 on 2010-01-16
No, the levels are fine. But when I try preferences->sound the system does not recognize any sound card. Weird!

---

### Post by gigi1234 on 2010-01-16
Ok the sound does work. But what doesn't work is click preferences->sound. That command does not detect sound and there is no sound device (volume control) at the bottom of screen on the panel. This is the only way I know to set the speakers to the bluetooth speaker instead of the laptop internal speakers.

---

