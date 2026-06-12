---
title: "network manager applet does not remember password"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by guus hendriks on 2011-08-01
L.S.
I'm working with Network Manager applet 0.7.0.100
every time I start my pc, I have to fill in the password to my wireless network
how can I make this network manager remember my network password??

---

### Post by barnex on 2011-08-01
You need to make sure that gnome-keyring-daemon is running. If necessary, add it to the programs started at login.

-Arne.

---

### Post by ajgreeny on 2011-08-01
I suspect you may also need to use the right click and "Edit connections" on the network manager icon, then check that the network you are using is set to "Automatically connect" and "Available for all users"

---

### Post by cybergalvez on 2011-08-01
I hate the default network manager, it usually the first thing I change when I do a fresh install for wicd

---

