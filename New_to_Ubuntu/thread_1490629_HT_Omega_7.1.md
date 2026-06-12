---
title: "HT Omega 7.1"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Feyerbrand on 2010-05-22
I have an HT Omega Striker 7.1 sound card with the driver cd and everything.  It installed via windows 7 ultimate 64 bit, and I was hoping that I could use the device in ubuntu to set up my recording studio.  The device is not recognized and the cd doesn't install the drivers.

---

### Post by cariboo on 2010-05-23
Can you post the result of:

```
lspci | grep "Audio device"
```

---

### Post by Feyerbrand on 2010-05-23
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
03:00.1 Audio device: ATI Technologies Inc HD48x0 audio

---

### Post by SlidingHorn on 2010-05-23
There's another thread here that shows they have Linux drivers specifically, although there's no mention of whether or not anyone's been successful using them.  Here's the link: [http://ubuntuforums.org/showthread.php?t=898046](http://ubuntuforums.org/showthread.php?t=898046)

---

