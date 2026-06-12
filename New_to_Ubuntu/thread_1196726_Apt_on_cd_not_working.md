---
title: "Apt on cd not working"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by awinstephen on 2009-06-25
I installed apt on cd from synaptic on jaunty, but it seems to have a problem when loading. It closes at 25%! Does anyone know what the problem is? Is there any other way to store my installed repositories with all the dependencies on cd or usb and use it in a freshly installed ubuntu?

---

### Post by 67GTA on 2009-06-25
Is the application freezing, or the aptoncd CD? Try running aptoncd from a terminal to see if it has any error messages. ```
aptoncd
``` If you have an apt CD made, you can copy the packages to /var/cache/apt. If you don't have a CD made yet, and have a system with the packages already on it, then they will be in /var/cache/apt. Copy them to your media of choice and paste them in /var/cache/apt on the new system. You will have to be root, or use gksudo to do this.

---

### Post by awinstephen on 2009-06-25
Thanks for the info. I installed the version from their website. working fine. good to know that just copy paste will do. thanks again....

---

### Post by Cheesemill on 2009-06-25
As an alternative check out Keryx.
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by awinstephen on 2009-06-28
> **Cheesemill said:**
> As an alternative check out Keryx.
[http://keryxproject.org/](http://keryxproject.org/)

thanks a lot.....

---

