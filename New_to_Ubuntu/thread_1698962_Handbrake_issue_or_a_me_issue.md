---
title: "Handbrake issue or a me issue"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by Shortstraw8 on 2011-03-03
I was running hand brake and trying to rip a dvd and it wouldn't, so I tried to stop it and it wouldn't so I right clicked and quit the app itself but my activity window is stuck open I can't close it, I can right click it and move it resize it. Im new to Ubuntu is there a way to get it off the screen from terminal?


Ubuntu 10.10 
Amd phenom 11 6 core
Asus mobo
Handbrake 9.5 
 
Is there a good command reference anywhere?


Just restarted my computer.

---

### Post by Perfect Storm on 2011-03-03
System ---> Administration ---> System Monitor

Look under Processes
Right click on the Handbrake and choose "Kill Process".

---

### Post by JohnAStebbins on 2011-03-03
> **Shortstraw8 said:**
> Im new to Ubuntu is there a way to get it off the screen from terminal?

The HandBrake gui executable is "ghb".  So from the terminal you can:
```

killall ghb

```

---

