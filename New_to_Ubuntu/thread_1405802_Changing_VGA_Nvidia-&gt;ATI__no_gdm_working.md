---
title: "Changing VGA Nvidia-&gt;ATI : no gdm working"
date: 2010-02-13
forum: New to Ubuntu
---

### Post by aktorun on 2010-02-13
Hi folks;

Recently I have changed my VGA card from NV8800GT to ATI5770.

My ubuntu was working quite fine with NV drivers.

But now, I even couldn't start gdm (no GUI).

I see errors in SYSLOG :
kernel : [....] NVRM: No NVIDIA graphics adapter found!
kdm[...] : X server died during startup


$lspci : grep VGA
01:00.0 VGA compatible controller : ATI Technologies Inc Device 68b8

What should I do to install driver for my new ATI card?
Please keep in mind that I have only CLI but no GUI.

---

### Post by rajeev1204 on 2010-02-13
Hi

From the console , type sudo nano /etc/X11/xorg.conf , change the line where it says nvidia to vesa.

Then type startx and it should start the gdm.

Then go to system>admin>hardware drivers and install the ATI driver, restart system.

If this doesnt work, come back here.

---

