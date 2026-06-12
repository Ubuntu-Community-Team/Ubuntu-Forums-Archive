---
title: "Low-graphics mode/xserver"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by spacefrog on 2011-05-29
Hi, I have very limited knowledge of linux so please bear with me. 

I activated the firewall on Ubuntu 10.04 for the first time this morning, and now I have lost access to my desktop. The first message reads "Ubuntu is running in low-graphics mode" and the error message is:
(EE) RADEON(0): [dri] RADEONDRIGet Version failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed
(EE) GLX error: Can not get required symbols.

While fiddling with the limited options I have I get another window mentioning xserver and the need to reconfigure it or something like that.  

After that the display tells me to stand by for one minute while the display restarts, but then it never does...

Can anyone help? Thanks in advance.

---

### Post by wildmanne39 on 2011-05-29
> **spacefrog said:**
> Hi, I have very limited knowledge of linux so please bear with me. 

I activated the firewall on Ubuntu 10.04 for the first time this morning, and now I have lost access to my desktop. The first message reads "Ubuntu is running in low-graphics mode" and the error message is:
(EE) RADEON(0): [dri] RADEONDRIGet Version failed to open the DRM
(EE) RADEON(0): Acceleration initialization failed
(EE) GLX error: Can not get required symbols.

While fiddling with the limited options I have I get another window mentioning xserver and the need to reconfigure it or something like that.  

After that the display tells me to stand by for one minute while the display restarts, but then it never does...

Can anyone help? Thanks in advance.

Hi go into restricted drivers if there is a driver for your video card activatte it, if it is activated deactivate it then reboot, then go back in and reactivate it. Did you by chance upgrade to natty?

---

### Post by spacefrog on 2011-05-30
> **wildmanne39 said:**
> Hi go into restricted drivers if there is a driver for your video card activatte it, if it is activated deactivate it then reboot, then go back in and reactivate it. Did you by chance upgrade to natty?

I hadn't upgraded, no. I had activated a firewall and done a backup, nothing else.

And after following instructions to uninstall and reinstall the proprietary drivers, the screen switches off when booting up, presumably due to inactivity, i.e. no communication.

---

### Post by wildmanne39 on 2011-05-30
> **spacefrog said:**
> I hadn't upgraded, no. I had activated a firewall and done a backup, nothing else.

And after following instructions to uninstall and reinstall the proprietary drivers, the screen switches off when booting up, presumably due to inactivity, i.e. no communication.
Hi,see if you can start is by typing start x
here is a link to get into recovery mode.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

