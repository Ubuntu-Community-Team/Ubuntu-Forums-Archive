---
title: "Using Suspend multiple times unexpectedly Shuts Down"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ronin510 on 2010-01-18
I'm running Ubuntu 9.10 on a Dell GX270 desktop (3.0 Ghz P4 + nVidia 6200).  Using various guides I found on the forum, I've been able to get Suspend to RAM to work (sometimes) with the proprietary nVidia driver v185 drivers.

I can Suspend to RAM, wake up, and everything works.  If I try Suspend a 2nd or 3rd time (it sometimes works a 2nd time), the system shuts down improperly and I have to press the power button to boot.

I have these packages installed:
```
acpi-support
acpi
gnome-power-manager
```

Has anyone had this problem and maybe found a solution?

---

### Post by ruru on 2010-02-13
I have the same problem.

I want to start using suspend on a desktop (Asus M2N32-SLI Deluxe motherboad and Nvidia 9500GT GPU with 185.18.36 driver) which is running a fresh 64-bit install of karmic with compiz enabled.
I can suspend/resume perfectly once, but the second attempt always fails. The screen goes blank with a flashing cursor, does not properly suspend, and is unable to be woken from this state.

I am keen to help debug this if anyone out there has suggestions where to start...

---

