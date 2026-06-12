---
title: "800x600 Resolution -- need more."
date: 2009-08-27
forum: New to Ubuntu
---

### Post by stoneface22 on 2009-08-27
Hi all --
     I just switched to Ubuntu 9.04 from a 64 bit version of Vista.  For some reason, Ubuntu won't allow me to select a higher resolution than 800x600.   I've got a 17.4" screen and an nvidia graphics card (dunno which).  I've tried other solutions on different threads, but everyone's problem seems to be different.
     I'm also looking to get my touchpad working with the multitouch scrolling (like most macs have), and to mount my files from the Vista partition; if these are simple matters I'd like to resolve them as well.  Thanks!
          --Keith

](*,)

---

### Post by NoaHall on 2009-08-27
System -> Admin -> Hardware Drivers

that will give you the driver. then nvidia x server settings will let you change, or system -> pref -> display.

---

### Post by tuxxy on 2009-08-27
Enable your video driver at system > prefs >hardware driver then install nvidia-settings package using synaptic, or run this command in terminal;

```
sudo apt-get install nvidia-settings 
```Once installed open nvidia-settings usually in system > admin > nvidia, here you can edit all types of display options including resolution, Hz etc  Is much better than the standard display tool.

---

### Post by gali98 on 2009-08-27
+1 for above.
See here for the multitouch...
[https://help.ubuntu.com/community/SynapticsTouchpad#Advanced](https://help.ubuntu.com/community/SynapticsTouchpad#Advanced) Configuration with a Graphical Interface

(See the part about gsynaptic... If I remember right it has multitouch options.)

Kory

---

### Post by Mark Phelps on 2009-08-27
Just a bit of "friendly advice" for someone new to the forum ...

Folks here tend to reply to threads based on the thread title.  So, folks knowing how to solve your other problems are likely to NOT respond to this thread.

You will likely get better and faster response if you start a new thread for each problem.

---

### Post by stoneface22 on 2009-08-27
Thx to all (incl mark).  Everything was explained simply and logically -- gotta love that.

---

