---
title: "What is the default screen resolution?"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by anders_r_r on 2009-06-12
In Xfce Settings Manager->Display the highest available resolution in the list is 1152x768. However, the Default option in the top of the list clearly results in a higher resolution. How does one tell what is the actual resolution?

Thanks,
Anders

---

### Post by kerry_s on 2009-06-12
it defaults to the highest supported by the vid card+monitor.
you should look up the recommended for your monitor and set it in xorg.conf.

---

### Post by x33a on 2009-06-12
search google for the resolutions supported by your monitor, then select the appropriate resolution.

---

### Post by kerry_s on 2009-06-12
> **x33a said:**
> search google for the resolutions supported by your monitor, then select the appropriate resolution.

xfce4 currently doesn't save that setting so ya have to do it in xorg.conf or use a xrandr script in the startup.

---

### Post by anders_r_r on 2009-06-12
Thanks for your answers!

In particular I would like to know what resolution is used when I chose the default option.

/Anders

---

### Post by kerry_s on 2009-06-12
> **anders_r_r said:**
> Thanks for your answers!

In particular I would like to know what resolution is used when I chose the default option.

/Anders

in the terminal:
**cat /var/log/Xorg.0.log | grep Default**

hey what version xfce4 are you running?
mine don't have a default on the list.

---

### Post by anders_r_r on 2009-06-14
> **kerry_s said:**
> 
hey what version xfce4 are you running?
mine don't have a default on the list.

Xfce 4 Desktop Environment version 4.4.2 (Xfce 4.4)

Thanks very much for the answer.

/Anders

---

