---
title: "Starting GUI from CLI"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by jenova_skill on 2009-01-30
I recently had some GFX driver issue's and I uninstalled the GFX drivers on purpose However im stuck in CLI (command interface) how do i start the GUI Ubuntu.

---

### Post by taurus on 2009-01-30
```
startx
```

---

### Post by Gulyan on 2009-01-30
for gnome:
sudo /etc/init.d/gdm start

for kde:
sudo /etc/init.d/kdm start

---

