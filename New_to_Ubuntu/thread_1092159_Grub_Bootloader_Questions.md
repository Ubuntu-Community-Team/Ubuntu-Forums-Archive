---
title: "Grub Bootloader Questions"
date: 2009-03-10
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-10
Hey,
wondering how I change the boot screen time (default is 30 seconds?)

I want to make it less.


Also, I want a better bootloader, or how can I use the Vista bootloader instead?

---

### Post by skymera on 2009-03-10
```
 sudo gedit /boot/grub/menu.lst 
```
Look for "Timeout" and change.

A better bootloader? It shows for a few seconds and works fine. Why would you want/need to change it?

---

### Post by ivanvajar on 2009-03-10
You can't use Vista bootloader. The only way to use Vista bootloader is to install Ubuntu with Wubi, but it reduces performances.

---

### Post by mikechant on 2009-03-10
> You can't use Vista bootloader.

Actually you should be able to use the Vista bootloader in conjunction with windows program EasyBCD or equivalent - this allows you to create Linux entries for the Vista bootloader.

---

### Post by kidambi502002 on 2009-03-10
If I may, there is also GRUB Editor available in GUI format which is easier to work with.  I have installed it from the Ubuntu packages and it is working nicely.

---

### Post by Gp. on 2009-03-10
How do I get the Grub editor?

---

### Post by rolnics on 2009-03-10
Use Synaptic Program Manager to install it.

System -> Administration -> Synaptic

Once it's load just do a search for it.

There's also Startup-manager this can be found the same way or using the terminal (Apps -> Accessories -> Terminal) enter this code: -

```
sudo apt-get install startupmanager

```

OR

If you really want to get to learn a bit more about Grub and startup manager [take a look at this HOWTO]("http://ubuntuforums.org/showthread.php?t=818177")

---

