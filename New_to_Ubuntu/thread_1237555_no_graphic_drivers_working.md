---
title: "no graphic drivers working"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by alaukik.kot on 2009-08-11
i upgraded my system from ubuntu8.1 to ubuntu 9.04 and works on kernals named as 

ubuntu 9.04 kernal generic 2.6.28-14
ubuntu 9.04 kernal generic 2.6.28-14 (recovery mode)
ubuntu 9.04 kernal generic 2.6.28-13
ubuntu 9.04 kernal generic 2.6.28-13 (recovery mode)
ubuntu 9.04 kernal generic 2.6.27-14
ubuntu 9.04 kernal generic 2.6.27-14 (recovery mode)
  

but any of them i can see the message ubuntu is working on low graphic mode... i tried to remove the driver and install again from hardware drivers and the recommended one.... but i really couldn't see any difference now it is showing me message that " this driver was just disabled, but still in use" i tried to install that recommended NVIDIA accelareted graphic driver version 180; even from synaptic but not much of help...
please help...

---

### Post by alaukik.kot on 2009-08-11
when ever i click on that activate button, it starts downloading and installing and then in span of seconds it terminates...

---

### Post by Buuntu on 2009-08-11
You could try an older version in Hardware Drivers.

---

### Post by alaukik.kot on 2009-08-11
any older or newer version of driver i tries to activate, downloading and installing process starts and terminates in seconds :)
  what to do about it?
 please help me out,

---

### Post by Buuntu on 2009-08-11
I'm guessing you already tried reinstalling the drivers?  Like deleting them and then installing them again?

---

### Post by alaukik.kot on 2009-08-11
yes i did install them. via synaptic and other sources too..

---

### Post by ajgreeny on 2009-08-11
I wonder if you need to stop gnome and gdm before you try to install the new driver by using Ctrl+Alt+F1 to get a command line, then login with username and password, (pw will not show on screen) then stop graphics with ```
sudo /etc/init.d/gdm stop
```.  Now install the new driver with apt-get.  You should now be able to restart the graphics with ```
sudo /etc/init.d/gdm start
``` and then if needed try ```
startx
```

---

