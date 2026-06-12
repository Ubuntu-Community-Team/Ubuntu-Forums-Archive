---
title: "remote connection (how do i turn on GUI?)"
date: 2008-06-09
forum: Networking &amp; Wireless
---

### Post by brexsis on 2008-06-09
i use vnc viewer for remote connection for now, but i like to turn off my GUI (CTRL + ALT + F5) sometimes, because with my desktop effects it eats up to 17% from CPU power. i would like to know if i turn of GUI, go somewhere to another PC, can i somehow turn on GUI through remote connection? when i try to connect with VNC viewer it shows me just black screen after i am typed IP and password. maybe somehow with putty or something like that i can do it?

---

### Post by Rocket2DMn on 2008-06-09
If you SSH into the machine, you can start X and Gnome back up with
```
sudo /etc/init.d/gdm start|stop|restart
```
Also, you can disable desktop effects by reverting to metacity
```
metacity --replace &
```
and re-enabled desktop effects with
```
compiz --replace
```

---

