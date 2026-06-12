---
title: "UBUNTU 8.10 does not have sound in my fresh install"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Art3mis on 2009-03-21
When using ```
aplay -l
```

I get ```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

What should I do so that sound will work??

---

### Post by Kosimo on 2009-03-21
> **Art3mis said:**
> When using ```
aplay -l
```

I get ```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

What should I do so that sound will work??


Go to System - Administration  -  Software Sources

Now go to the Updates Tab and select all boxes (pre-releases and unsupported updates as well)

Then close and hit reload
New updates will appear, then update your system and restart ;)


Looks like your problem should be solved with new kernels updates which are available under pre-release.

---

### Post by Kosimo on 2009-03-21
By the way, here the discussion that talks about this:


[https://answers.launchpad.net/ubuntu/+question/55728](https://answers.launchpad.net/ubuntu/+question/55728)

---

