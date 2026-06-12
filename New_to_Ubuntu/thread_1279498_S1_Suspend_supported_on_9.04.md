---
title: "S1 Suspend supported on 9.04?"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-09-30
Does anyone know if S1 Suspend mode is supported on Ubuntu 9.04?

S3 doesn't work for my motherboard so I had to switch to S1. S1 works on Win XP but in Ubuntu there is no option to suspend when the BIOS is set to S1.

---

### Post by Cuco3 on 2009-10-01
Please?

---

### Post by Cuco3 on 2009-10-02
Please?

---

### Post by peculiar penguin on 2009-10-02
Open a terminal and try
```
gnome-power-cmd suspend
```

---

### Post by Cuco3 on 2009-10-02
Thanks for the reply. Here's the result:

> gnome-power-cmd suspend

Suspending
Error org.freedesktop.PowerManagement.NoHardwareSupport: Suspend is not available on this computer
FailedI know S1 works and the hardware supports it because it suspends in WinXP.

---

### Post by peculiar penguin on 2009-10-02
No idea then, sorry.

The [Gnome Power Manager FAQ]("http://live.gnome.org/GnomePowerManager/FAQ#head-5d4d7bb306ca154c956e3ef69dae036942f6cf40") has a few other hints, but I don't know if/how they apply to Ubuntu, so proceed at your own risk...

---

### Post by Cuco3 on 2009-10-02
Thanks anyways, I think it has something to do with PM-Utils not supporting S1 Standby. I remember reading on the Ubuntu Wiki on how to set up the old power management software in previous Ubuntu versions so I'll give that a try.

---

