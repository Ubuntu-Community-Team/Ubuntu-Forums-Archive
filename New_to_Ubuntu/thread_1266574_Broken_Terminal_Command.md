---
title: "Broken Terminal Command"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by pstefanini on 2009-09-14
I tried to install Java6 JRE.  Instead of entered:

[B]sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
[/B]
Things happened but I mistakenly closed the terminal and now it indicates the following when I try to repeat the above command:

**E: dpkg was interrupted,you must manually run 'sudo dpkg --configure -a' to correct the problem.**

Does anyone know what I should do to either continue or remove any broken processes? Thank you.

---

### Post by drs305 on 2009-09-14
Open a terminal: Applications, Accessories, Terminal.

Run the command as the error message states:
```

sudo dpkg --configure -a

```
Type your password when prompted, even though you won't see it, then ENTER. If you get further error messages, please post them.


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by pstefanini on 2009-09-14
IT WORKED drs305!!!!  Thank you !!!!

---

