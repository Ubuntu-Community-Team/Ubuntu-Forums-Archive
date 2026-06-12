---
title: "what is wrong with this"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-01-16
i am trying to stop the system beep in ubuntu i read on a site that i could use the command sudo rmmod pcspkr to temporarily disable it from the terminal. i tried to write a script and saved it in sessions to do the same
thing but doesnt work. see below. 

#!/bin/bash 
sudo rmmod pcspkr

what did i do wrong/tks cheesemaker

---

### Post by rburkartjo on 2009-01-16
this could be the problem

ray@ray-desktop:~$ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules
ray@ray-desktop:~$ 


even so is there a way to turn off this annoying beep/tks cheesemaker

---

### Post by Drubie on 2009-01-16
> **rburkartjo said:**
> 
even so is there a way to turn off this annoying beep/tks cheesemaker

I went a GUI way:

System > Preferences > Volume Control

under the Alsa Mixer, I muted 'Beep'
If 'beep' doesnt show up, try clicking the preferences button in the window and find the checkbox next to beep.  

that worked for my hardware, I dont know about yours though.
If it doesnt work for you, a guru will show up soon.

goodluck

---

### Post by albinootje on 2009-01-16
> **rburkartjo said:**
> 
ray@ray-desktop:~$ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules


Just tested it :
> 
$ sudo rmmod pcspkr
-- and again --
$ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules

As you can see, it's possible that the module was already unloaded.

---

### Post by rburkartjo on 2009-01-16
tks guys maybe it does work/cheesemaker

---

### Post by snova on 2009-01-16
Well, besides the fact that the pcspkr module might already be unloaded, there is one flaw in this script.

When you run sudo, it asks for your password. If you have it run automatically, it won't ever get it! :)

Instead, here is an alternative solution. Open "/etc/modprobe.d/blacklist" as root (gksudo gedit /etc/modprobe.d/blacklist) and add this line to the end:

```
blacklist pcspkr
```

This puts the module on a blacklist, so it will never be loaded in the first place.

---

