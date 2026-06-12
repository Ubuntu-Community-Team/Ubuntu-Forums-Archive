---
title: "Skype sound problem"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by Old-un on 2011-06-22
Have just installed Skype 2.2 beta and i can't get to hear my own voice in the playback of test call. How do i disable alsa and how would i install PulseAudio anyone please.

---

### Post by cariboo on 2011-06-22
It would help if you told us what version of Ubuntu are you using. Previous to Natty, open an Applications->Accessories->Terminal and type:

```
alsamixer
```

Once alsamixer is open use the arrow keys to navigate between sections, and to turn the volume up and down. Make sure the microphone it turned up to the level you want. Once you are happy with the settings, press esc to exit, then in the same terminal type:

```
sudo alsactl store
```

to save the settings.

In Natty and newer, click the speaker icon in the notification area, and select Sound Settings, then click the input tab, and turn the input volume up to where you want it. 

One other thing to check is in skype make sure auto-volume levels are disabled.

---

