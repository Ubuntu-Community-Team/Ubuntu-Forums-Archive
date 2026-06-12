---
title: "Ati driver install"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by 6027 on 2009-12-18
> **6027 said:**
> I have an ATI HD9650 in my laptop. I'm having a lot of trouble installing the drivers from ATI. I've downloaded both the x_86 and 64 and niether one installs WTF is up?

i get this
[IMG]http://img94.imageshack.us/img94/7626/screenshotsu.png[/IMG]


I am using a 32bit system, what do I do?

---

### Post by halitech on 2009-12-18
Did you make the file executable after downloading it? Right click - properties -> Permissions tab, allow executing.

---

### Post by dream_coder on 2009-12-18
I installed it earlier ... Make sure you remove previous Propriertary Drivers first then open a terminal cd to the directory the script is in then just run sudo sh ./atifilename.sh and it should bring the install setup to the screen

---

### Post by skymera on 2009-12-18
Ok, i've used ATi and Nvidia with Ubuntu since 2007 and this method has always worked:

Use Envy. It's in the repos, check in Synaptic and install EnvyNG.
Run that program and it will download, compile and install the kernel modules/drivers for you.

For terminal:
```
 sudo apt-get install envyng-core 
 sudo envy -t 
```

@ ATi: I had an HD4870 ATi card with Ubuntu. Compiz lagged bad and Flash videos would play slow and eat up 100% CPU, Games FPS were minimal. Not sure if newer drivers have helped at all.

---

