---
title: "How do i change drivers?"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by SDE on 2007-04-17
i just put in a cisco airnet 350 series pcmcia card and when i do an lshw -C network, the driver shows up as **e100**.  i thought it should be an airo_cs.

anyone have any idea how and if i can fix this?

---

### Post by josephus on 2007-04-17
You can load and unload drivers using the modprobe command

```
sudo modprobe -r e100
sudo modprobe airo_cs
```

---

