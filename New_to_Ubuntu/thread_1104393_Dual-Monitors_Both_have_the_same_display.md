---
title: "Dual-Monitors: Both have the same display"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Jk435 on 2009-03-23
I have Ibex installed and can not get my second monitor to have it's own display, its just a clone of the main one, and system/preferences/screen resolution only shows one monitor. When trying to figure it out, I ran across a lot of people saying to look in compiz settings manager/display settings but I don't seem to have display settings in compiz?

---

### Post by kanikilu on 2009-03-23
What kind of video card do you have?

I have an nvidia and  used *nvidia-settings* to setup dual monitors on my computer...

---

### Post by Jk435 on 2009-03-23
Sorry, I have a  Mobility Radeon HD 3450

---

### Post by Kareeser on 2009-03-23
Have you installed the necessary drivers?

System -> Administration -> Hardware Drivers

---

### Post by kanikilu on 2009-03-23
> **Jk435 said:**
> Sorry, I have a  Mobility Radeon HD 3450 I'm not familiar with ATI, sorry, maybe someone else can help with that.

I want to say there should be some sort of ATI "control panel" to do this...I'm just not sure how to install it (if necessary) or where to find it if it's already installed...

---

### Post by Jk435 on 2009-03-23
I have the ati/amd proprietary FGLRX graphics driver enabled in hardware drivers.

---

### Post by kanikilu on 2009-03-23
I found an old post that says the control panel is called "fireglcontrolpanel". Not sure if that's still the case, but maybe try running that...

---

### Post by Jk435 on 2009-03-23
Thanks guys, you both helped me find it.. the ATI Catalyst Control Center in applications/accessories got it working ;)

---

### Post by t0p on 2009-03-23
If you go to **System > Preferences > Screen Resolution** you will open the **Monitor Resolution** window.  Now untick the box in the upper left corner of the display, where is says Mirror Screens.  Now click Apply.

Does that fix your problem?  I had a similar problem, where 2 monitors had different displays when I wanted them to be the same.  I ticked the Mirror Screens box and that fixed it.  Which is why I think *unticking* it will sort you out.

**EDIT**: I was too late *and* I was wrong.

I hang my head in shame.  :(

---

