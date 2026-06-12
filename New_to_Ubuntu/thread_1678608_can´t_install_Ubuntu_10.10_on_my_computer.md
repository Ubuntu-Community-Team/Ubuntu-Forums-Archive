---
title: "can´t install Ubuntu 10.10 on my computer"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by maserinn on 2011-01-30
I am trying to install Ubuntu on my computer because I´ve always wanted to try it out but I always get the same error regarding the graphics card. DVI - 1 - DV probed a monitor but no EDID. I have a ATI RADEON 2100 graphics card.
What to do?

---

### Post by sandyd on 2011-01-30
> **maserinn said:**
> I am trying to install Ubuntu on my computer because I´ve always wanted to try it out but I always get the same error regarding the graphics card. DVI - 1 - DV probed a monitor but no EDID. I have a ATI RADEON 2100 graphics card.
What to do?
try setting nomodeset at the livecd startup
Press ESC when you see the purple screen.
Press whatever key corresponds to "other options"
and select nomodeset.
p.s. I have the error too
```

[drm:radeon_dvi_detect] *ERROR* HDMI-A-1: probed a monitor but no|invalid EDID

```
but the monitor works anyways...

---

