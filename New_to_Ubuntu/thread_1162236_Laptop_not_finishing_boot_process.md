---
title: "Laptop not finishing boot process"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by cwrann on 2009-05-17
I just upgraded my Laptop to Xubuntu's Hardy Heron. The start up seems to go fine until it gets to the local boot script at which point i am repeatedly given this message:

```
b43-phy0 ERROR: You must go to HTTP://linuxwireless.org/en/users/drivers/b43#devicefrimware and download the correct firmware.

b43-phy 0 ERROR: Frimware file "b43/ucode5.fw" not found or load failed
```

Is there a way to circumvent this message and finish the boot process? I can't see why the wireless card is necessary to booting up the laptop. Besides, I can't install the appropriate drivers unless the computer finishes booting anyway.

---

### Post by charliehorse55 on 2009-05-17
Have you tried booting into safe mode? 

When GRUB is loading, press escape and select the first option from the top that ends with "(Safe Mode)".

Hopefully this will boot.

---

### Post by cwrann on 2009-05-17
All I have is (recovery mode) no (safe mode) is this the same?

---

### Post by cwrann on 2009-05-17
is there a way to tell the boot process to ignore this from the command line?

---

### Post by charliehorse55 on 2009-05-17
> **cwrann said:**
> All I have is (recovery mode) no (safe mode) is this the same?

Yeah. Haven't had to use that screen in a long time....

You should be able to edit your wireless driver settings, but I don't know anything about that. Try plugging into an ethernet cord when in recovery mode, so that you can download/install the drivers required.

---

### Post by cwrann on 2009-05-18
unfortunately this laptop does not have an ethernet port.

---

