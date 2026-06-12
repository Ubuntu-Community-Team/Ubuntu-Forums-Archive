---
title: "Ubuntu wont uBOOTu"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-04-06
I've had a working version of Ubuntu for a while now. Today it wont boot. It goes to the boot screen with the moving dots and never stops.

I'm thinking about booting from a liveCD, but what should I do then. I don't want to do a fresh install. How can I trouble shoot this.

---

### Post by cgroza on 2011-04-06
Can you go into recovery mode? You can do it by selecting it at the grub prompt.
Also, any changes to the state of our system lately? Removed programs, installed others?

---

### Post by alphacrucis2 on 2011-04-06
> **wlraider70 said:**
> I've had a working version of Ubuntu for a while now. Today it wont boot. It goes to the boot screen with the moving dots and never stops.

I'm thinking about booting from a liveCD, but what should I do then. I don't want to do a fresh install. How can I trouble shoot this.


First thing would be to hold down SHIFT as the machine starts to boot to get GRUB to display the boot menu. Try booting the recovery option.

---

### Post by Mark Phelps on 2011-04-06
If you can actually get into recovery mode, when presented with options, choose the one to repair broken packages -- I've found that tends to fix most of these problems with 10.10.

Then, select the option for normal boot and you should be OK after that.

---

