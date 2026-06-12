---
title: "disable touchpad"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by LittleGyko on 2010-07-13
my mouse touchpad is giving me a lot of problems while i type and so i would like to disable it. however, i am not able to find an option to do that in System>Preferences>Mouse.the option to disable while typing is not working. 

my system details are 
dell studio 14 laptop
ubuntu 10.04

---

### Post by nothingspecial on 2010-07-13
Hi, try using syndaemon.

```
syndaemon -d -t -i 3
```

The number 3 at the end of the command is the amount of time in seconds you would like to disable the track 
pad for after you have pressed a key.

Add the command to system > preferences > startup applications if you want to
make it permanent.

---

### Post by LittleGyko on 2010-07-14
thanks...i am not sure if that worked, will get back to you.

---

