---
title: "[SOLVED] Modprobe every time i start ubuntu"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by abrasax on 2008-09-26
This isn't really about wireless. I installed my wireless card with ndiswrapper, and it works really well. Just one problem, every time i start ubuntu i have to run a command in terminal:

modprobe ndiswrapper

So i would like to know how to create a script with this command and run it automatically at startup.

Thank you for your help.

---

### Post by issih on 2008-09-26
A simpler solution would be to add ndiswrapper to the list of modules that get loaded at boot time.

to do that do:

```
sudo gedit /etc/modules
```

then just add "ndiswrapper" at the bottom of the list on a new line.
now when you reboot ndiswrapper will be modprobbed automatically

Hope that helps

---

### Post by willca on 2008-09-26
Edit /etc/modules
Add ndiswrapper at the end.

---

### Post by abrasax on 2008-09-26
Thanks. Very nice solution.

---

