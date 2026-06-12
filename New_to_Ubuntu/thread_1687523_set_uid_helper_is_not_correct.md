---
title: "set uid helper is not correct"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by nnjond on 2011-02-14
Hi,

What does this mean??? 

I was prompted to dl some updates after a fresh install but it was only partially successful, and when I rebooted, the screen froze with the mssge:

Cannot open Konsolekit session

Permission of the setup uid in not correct.

Can this be solved from alive cd or Grub menu?

---

### Post by cariboo on 2011-02-14
Reboot, and open a terminal and type:

```
sudo apt-get -f install
```

---

### Post by nnjond on 2011-02-14
Thanks for your advice. I can't access a console -via ctrl-alt-Fx
Can i issue that command from a live cd?

---

