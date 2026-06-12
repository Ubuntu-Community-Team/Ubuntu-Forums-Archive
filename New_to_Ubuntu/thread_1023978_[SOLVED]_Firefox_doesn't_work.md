---
title: "[SOLVED] Firefox doesn't work"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-28
just installed xubuntu and attempted to copy and paste settings files from the .firefox folder. when trying to run firefox I get a error notice saying that it is already running and to close it. I tried uninstalling and reinstalling firefox AND removing the copied folder .firefox, (with settings) with no success. any help is appreciated.

---

### Post by Old_Grey_Wolf on 2008-12-28
If you are using Synaptic to remove Firefox, are you selecting "Mark for Complete Removal"?

---

### Post by Pobega on 2008-12-28
Run *killall firefox* from a terminal, then try running Firefox again. Hopefully it will work. This happens sometimes with Firefox, especially when it crashes.

---

### Post by northern lights on 2008-12-28
Running ```
killall firefox
```doesn't kill it?
Even after rebooting and not having run firefox before you receive this error?

Complete removal:```
sudo aptitude purge firefox
```

---

