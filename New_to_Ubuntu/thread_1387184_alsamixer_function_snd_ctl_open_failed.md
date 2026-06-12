---
title: "alsamixer: function snd_ctl_open failed"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by Mariane on 2010-01-21
```

alsamixer

```
alsamixer: function snd_ctl_open failed for default: No such device

```

alsamixer -c 0

```
I get the equaliser but the headphones are set to level zero, not muted but won't go up. 
And whatever I mute I get either no sound out of the laptop speakers with "say" or a double sound. 

```

say tee

```

The sound which comes out is "tee tee" instead of "tee".

```

 aplay -l

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Am I misreading this or does it look like I have 2 sound cards BOTH numbered zero???
Please help, this is driving me crazy. 

Mariane

---

