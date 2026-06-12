---
title: "Audio not working with multiple audio programs open"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Zopiac on 2009-07-28
I am trying to record my bass input to a track in Audacity, but I need a metronome in order to keep the beat. However, when I try to use GTick to use as a metronome, (or even making a simple beat in Hydrogen) Audacity refuses to record, and states that another program is using the audio. Can't two programs use audio at once?!? This is really ticking me off.

Using Ubuntu Studio 9.04, Pulse Audio.

---

### Post by Zopiac on 2009-07-28
OK, now Audacity is giving me the following error when I try to record at all:

```
Error while opening sound device. Please check the input device settings and the project sample rate.
```

They are the same as they were before, and the mic works in other programs, but suddenly Audacity doesn't want to comply. Again.

Linux REALLY isn't the best OS for Audio related projects, is it? I've had countless problems with it over the past two years of using Linux. :mad:

EDIT: Fixed, I changed the memlock variable in the Ubuntu Studio Controls. Original problem persists.

EDIT2: New problem, when I hit record or play in Audacity, it just STOPS about a tenth of a second in, without even giving any output for that small period of time.

---

