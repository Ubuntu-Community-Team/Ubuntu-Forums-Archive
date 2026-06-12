---
title: "Calibrate OSD?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-05-05
Hi. I'm very glad the Onscreen Display works for my T30 out of the box! I notice however when I up or down the brightness/or volume the display does not correspond with my actions.

This is especially true with the brightness setting. I also don't want the screen to default to extremely bright whenever I log on. Is there a way to save the current setting when I log out?

One more question. Whenever I power off there is an annoying system beep. Where do I go to turn/disable that on Power off?

Thanks.

---

### Post by tomcheng76 on 2009-05-05
for turning off the beep
> gksudo gedit /etc/modprobe.d/blacklist.conf
append a line "blacklist pcspkr" (without quotes) to the end of the file
restart the pc


---

### Post by kpkeerthi on 2009-05-05
As for the LCD brightness, you should be able to set a default brightness in your BIOS.

---

### Post by emeraldgirl08 on 2009-05-05
> **tomcheng76 said:**
> for turning off the beep

Thanks. It worked :)

---

