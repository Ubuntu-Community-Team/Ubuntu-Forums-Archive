---
title: "startup programs"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Artanis.ro on 2010-03-27
Can someone tell me how can I  use the terminal to set a program to run each time ubuntu starts or how can I set it not to start once the system startsl? I know the programs are in /etc/init.d/. But how can I set them to start or not?

Thanks

---

### Post by wightghost on 2010-03-27
Hi there,
Try this: System > Preferences > Startup Applications.  

From there you can set what programs to start (or not).

Hope this helps. Good Luck :)

---

### Post by spiderbatdad on 2010-03-27
In /etc/rc0.d-rcS.d you will see the startup programs preceded by S or K for start or kill respectively...They are the links whose targets are in init.d. Changing the S or K in each of the run levels should do what you want. You will need to run sudo update-rc.d after any changes...see the readme files in each directory.
Alternatively try using upstart. sudo update-rc.d remove -f <program>

---

