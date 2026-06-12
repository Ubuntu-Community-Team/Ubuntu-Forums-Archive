---
title: "gnome system monitor shows xorg as root user"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by S0m3th1ngw13rd on 2009-03-05
should it run as my username instead?

---

### Post by Rocket2DMn on 2009-03-05
No, xorg is started by gnome (gdm) when the system starts up - that's why you see the graphical login screen before you even login.
You *can* run it as yourself, but there really isn't any need.  Most anything that boots with the system is run by root.

---

### Post by S0m3th1ngw13rd on 2009-03-05
thank you. I wasn't sure about that one.

---

