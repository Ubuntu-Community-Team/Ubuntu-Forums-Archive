---
title: "Nvidia Xserver settings won't save"
date: 2011-07-05
forum: New to Ubuntu
---

### Post by jermza on 2011-07-05
Every time I change my Nvidia Xserver "powermizer" from "adaptive" to "prefer maximum performance", the settings default back to "adaptive" when I log out.

I'm using 11.04 with dual GTX 460s (in SLI), so I can't see why it would revert to "adaptive" each time.

How do I make the settings stick?

---

### Post by aeiah on 2011-07-05
perhaps you need to launch the control panel with root privilages for it to save properly? i know you do with the standard nvidia control panel, because it saved to xorg.conf, which a standard user cant modify...
```

gksu nvidia-settings
```

---

### Post by thane1 on 2011-07-05
Not familiar with 11.04.  As I recall though in 10.10, when I tried to save the dualscreen info for ubuntu's proprietary nvidia driver (using the "nvidia Xserver settings" program), I had to create a new xorg.conf.  I believe 10.10 didn't create and use that file by default.  Maybe 11.04 is the same.  cheers

---

### Post by thane1 on 2011-07-05
Just checked on ubuntuforums and other people have reported a lack of a xorg.conf file to save their settings, when trying to set up dual screen.  I realize, that you are using two vid cards linked in sli mode instead, but possibly this might be a starting point.  cheers

---

