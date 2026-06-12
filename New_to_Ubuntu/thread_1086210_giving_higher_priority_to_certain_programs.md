---
title: "giving higher priority to certain programs"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by mity on 2009-03-03
my video playback get very choppy when i go full screen. in windows i am able to solve it by giving vlc a higher priority. however, when try to do the same things through system monitor, the priority remains unchanged. 

am i missing something?

---

### Post by mcduck on 2009-03-04
You need root privileges to give anything higher priority (lower nice value). Normal users are only able to lower a tasks priority.

---

### Post by sdennie on 2009-03-04
You can probably fix this problem with:

```

sudo renice -19 `pgrep vlc`

```

---

### Post by mity on 2009-03-04
i was able to increase my priority, but that did not fix my problem. 

does that mean there is a problem with my video driver?

---

### Post by skymera on 2009-03-04
Do you have Compiz enabled?

It sometimes get weird video playback when have Compiz enabled.

---

### Post by mity on 2009-03-04
nope, all of the effects are turned off

---

### Post by 3rdalbum on 2009-03-04
Try changing the video output module in VLC. Also note that Nvidia and ATI drivers for Windows support GPU-decoding for more formats than the Linux-based drivers - if your CPU is weak it might be having trouble keeping up.

---

### Post by mity on 2009-03-05
i have tried changing the outputs in vlc, and the problem remained.

i have also tried movie player, and i get the same glitches. 

i have been using ubuntu for over a year, and i only began to experience this glitch with in the last month. 

is there anything else i can do?

---

