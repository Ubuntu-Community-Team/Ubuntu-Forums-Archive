---
title: "X doesnt start automatically after updating the kernel"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by infestor on 2010-01-07
i have just updated my kernel to the latest (from update manager) but when ubuntu starts i have the black login screen. i normally have auto-login.  on the black screen it also says '1600*1200 splash mode failed now switching to 1280*1200'.
is there a way to fix this?
(or at least how do i start X from the command line?)

---

### Post by Hallvor on 2010-01-07
Try ```
startx
``` and see if you get any useful output.

---

### Post by infestor on 2010-01-07
i get: fatal server error: no screens found
:(

---

### Post by infestor on 2010-01-07
how can i probe the problem?

---

### Post by Hallvor on 2010-01-07
Try moving your xorg file: 

[HTML]sudo mv /etc/x11/xorg.conf /etc/X11/xorg.old[/HTML]

Then reboot.

If you get the same problem, you can copy it back with 

```
sudo mv /etc/X11/xorg.bak /etc/X11/xorg.conf
```

---

### Post by infestor on 2010-01-07
thanks that worked...but i would like to know why did i have to move the xorg file?

---

### Post by Hallvor on 2010-01-07
If it for example links to a proprietary graphics driver in the old kernel, it wouldn`t find it if you install a new kernel. Then you`ll get the no screens found error. When you move the xorg file, the computer will just make a new and clean one when you boot. I`ve had the same problem in Debian.

---

