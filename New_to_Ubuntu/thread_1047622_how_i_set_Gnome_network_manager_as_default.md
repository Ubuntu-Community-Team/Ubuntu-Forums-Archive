---
title: "how i set Gnome network manager as default?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by TechDragon on 2009-01-22
i am using Ubuntu 8.10 with the Kubuntu kde desktop 4.2 rc1 installed, kde's network manager is not working for me. 

How do I make Gnomes network manager the default in kde and and disable or remove the kde network manager?

---

### Post by snova on 2009-01-22
I've the same setup, had the same problem.

First, I uninstalled KNetworkManager- no sense keeping it.

Then, go to System Settings -> Advanced -> Autostart.

Click Add Program, and type in **nm-applet**, which is the Gnome one. From now on it should start with the KDE session.

---

