---
title: "Removing services I don't need"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by K7AAY on 2009-08-04
WPAsupplicant and other services I don't need are running. When I go to Synaptic to remove them, Synaptic tells me removing it will also remove useful stuff like the Network Manager and the Desktop Manager. How do I remove WPAsupplicant without breaking stuff?

---

### Post by wizard10000 on 2009-08-04
> **K7AAY said:**
> WPAsupplicant and other services I don't need are running. When I go to Synaptic to remove them, Synaptic tells me removing it will also remove useful stuff like the Network Manager and the Desktop Manager. How do I remove WPAsupplicant without breaking stuff?

First Rule of Geek Professionialism:  Never go someplace you can't get back from  :D

First try disabling the services.  I'd install Boot-Up Manager

> sudo apt-get install bum

It'll show up under System --> Administration.

Then you can shut off anything you like - but make sure you don't need it before you turn it off  :)

If wpasupplicant is installed but disabled it all it takes up a little bit of disk space.

If you're feeling really adventurous you can install sysv-rc-conf but that's a full-blown runlevel editor and you can really screw up a system with it if you don't know what you're doing.

---

### Post by K7AAY on 2009-08-04
Thank you!

---

