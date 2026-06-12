---
title: "How to install drivers?"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by ZenBuddhistDog on 2008-12-27
Hello,
I'm really new to ubuntu (2 hours)
and want to install the NVIDIA drivers i need for my GeForce 8500Gt.
I've done what they say to install the drivers, but in the terminal it just says it cannot read sh NVIDIA-Linux-x86_64-177.82-pkg2.run.
what am i doing wrong?

---

### Post by pdtpatrick on 2008-12-27
run sudo chmod a+x NVIDIA-Linux-x86_64-177.82-pkg2.run 

and then run the command you did earlier.

---

### Post by nhasian on 2008-12-27
can you just enable the built in proprietary drivers?  System->Administration->Hardware Drivers
you should be able to activate the drivers there.

if your going to use the ones from nvidia's website you cant install them while xwindows is running.  you'd have to press Control-Alt-F1 to switch to a terminal.  then type

```
sudo /etc/init.d/gdm stop
```

now you can run the installation script from nvidia.

if your in the directory where the script is located type:

```
./NVIDIA-Linux-x86_64-177.82-pkg2.run 
```

after its done start gnome back up with:

```
sudo /etc/init.d/gdm start
```

---

### Post by ZenBuddhistDog on 2008-12-27
I tried that and it replied:
chmod: cannot access `NVIDIA-Linux-x86_64-177.82-pkg2.run': No such file or directory
i know it exist, as it is sitting right there on my desktop.

---

### Post by Ender41 on 2008-12-27
> **ZenBuddhistDog said:**
> I tried that and it replied:
chmod: cannot access `NVIDIA-Linux-x86_64-177.82-pkg2.run': No such file or directory
i know it exist, as it is sitting right there on my desktop.

did you cd from the terminal to ~/Desktop ?

---

### Post by ZenBuddhistDog on 2008-12-27
Okay, i just used the ones Ubuntu came with, but i'm still having problems with Toribash and ActivePython.

---

