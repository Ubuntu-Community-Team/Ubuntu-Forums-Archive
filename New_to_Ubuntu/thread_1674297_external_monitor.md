---
title: "external monitor"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by N84Christ on 2011-01-23
i needto find out how to turn on the external monitor  so i can connect to tv. it worked when windows worked but now under ubuntu it does not. my system is presario f750 us

---

### Post by sandyd on 2011-01-23
> **N84Christ said:**
> i needto find out how to turn on the external monitor  so i can connect to tv. it worked when windows worked but now under ubuntu it does not. my system is presario f750 us
post output of
```

xrandr
```
while monitor plugged in

---

### Post by Rocket2DMn on 2011-01-23
When you plug in the external monitor (or tv), does the screen show in System->Preferences->Monitors ?
If you are using NVidia restricted drivers, you may need to check under System->Administration->NVIDIA X Server Settings.

---

