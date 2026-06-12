---
title: "Video display in ibex 8.10"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by barrykgerdes on 2008-12-05
I have just upgraded to Ibex from gutsy.
I have lost my 1024 x 768 display 
The display is locked at 640 x 480 with no options
I have a SiS 661 inbuilt video card (no opengl facility)
I have been upgrading regularly since dapper and have always been able to get a decent display. What has happenned this time and how do I fix it. 

Linux on a 640 x 480 screen - forget it! 

Barry

---

### Post by Xovan on 2008-12-05
Try activating the restricted drivers they might have been deactivated during installation of Ibex.  That is what's going on with me in kubuntu.

---

### Post by barrykgerdes on 2008-12-05
> **Xovan said:**
> Try activating the restricted drivers they might have been deactivated during installation of Ibex.  That is what's going on with me in kubuntu.


That's what I have been trying to do but don't know how. I have tried all the usual fixes but nothing improves. I haven't found any drivers at all.

seems so odd I have never had this bother before

Barry

---

### Post by doas777 on 2008-12-05
go to System -> Administration -> Hardware Drivers.

in the middle frame, click on the select the driver you wanna use and click 'Activate'. 

then close and reboot.

if a driver you need is not in the list, open a terminal and type:
```
sudo apt-get update
```
and then when the command is done, open Hardware Drivers again..

I've had instances that I've had to reboot a few times before a driver showed up.

good luck,
franklin

---

### Post by barrykgerdes on 2008-12-05
I have tried that many times

but nothing ever shows up in the drivers

barry

---

### Post by barrykgerdes on 2008-12-05
> **barrykgerdes said:**
> I have tried that many times

but nothing ever shows up in the drivers

barry

The display has come good. I fiddled with a few things.
The only thing I can see that may have fixed it was to change the monitor in xorg.conf from "generic" to "super vga monitor"

barry

---

### Post by doas777 on 2008-12-05
that is weird
what kinda card do you have? you may wanna try envygtk

---

### Post by barrykgerdes on 2008-12-05
> **doas777 said:**
> that is weird
what kinda card do you have? you may wanna try envygtk
See the Ist post.
SiS has very little support for Linux (No OpenGl)
Earlier releases of Ubuntu did have automatic support when installing. The upgrade of gutsy to ibex appears to have missed this.

In any case alls well that ends well!

Barry

---

