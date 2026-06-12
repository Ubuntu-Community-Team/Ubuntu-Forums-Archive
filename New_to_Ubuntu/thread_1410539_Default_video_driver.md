---
title: "Default video driver"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by ebates on 2010-02-18
How do I configure Ubuntu 9.10 to use my proprietary Nvidia driver instead of it's default driver.  Each time I start/restart Ubuntu I have to tweak the display to get the Nvidia driver.

Tx
EBates

---

### Post by sandyd on 2010-02-18
> **ebates said:**
> How do I configure Ubuntu 9.10 to use my proprietary Nvidia driver instead of it's default driver.  Each time I start/restart Ubuntu I have to tweak the display to get the Nvidia driver.

Tx
EBates
can you post the output of
```

cat /etc/X11/xorg.conf
```

---

### Post by ebates on 2010-02-18
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Tx
EBates

---

