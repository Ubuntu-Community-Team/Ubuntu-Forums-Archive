---
title: "hardware detection"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by libihero on 2008-12-23
i've been playing around with ubuntu and i really like it.  the only problem i have so far with it is that it still doesnt seem to be running as fast as windows.  when i boot windows, the programs on it just seem to run a lot smoother.
for example, sometimes clicking on my laptop mousepad doesnt work (i'm talking about tapping, not pressing the button).
is there any way for me to check if all of the hardware on my laptop is detected by ubuntu, or if there is a way for me to make it run faster
also i dont think my webcam is working, i have a gateway m-1625

---

### Post by gjoellee on 2008-12-23
try this link: [http://kshoster.net/content/optimize-ubuntu-804-hardy-heron-speed](http://kshoster.net/content/optimize-ubuntu-804-hardy-heron-speed)

you should also check your system resourses being used (System Monitor), check your CPU usage (how hard your prosessor(s) is/are working) and your memory(ram) usage.

---

### Post by timandjulz on 2008-12-23
A big culprit in slowing down one of my systems is not using video drivers specific to the hardware.  You can check this by going to "System-Administration-Hardware Drivers" and making sure everything there has a checkbox.

---

### Post by minsf on 2008-12-23
sorry if this is obvious, but have you already tried to check your hardware detection from the cli with
```

sudo lshw |less

```
?

---

