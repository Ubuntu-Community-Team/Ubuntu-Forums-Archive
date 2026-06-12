---
title: "OpgenGL without graphics driver"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-04-04
Question: I've a notebook with OpenSuse and one of those annoying NVIDIA drivers.

As always, the closed-source NVIDIA driver doesn't work.
I've compiled the kernel, recompiled and reinstalled the driver but that doesn't solve the problem. It seems the driver is buggy.

Is it possible to get some kind of generic OpenGL, without having to install the OpenGL drivers? Something like mesa ?

---

### Post by MooPi on 2010-04-04
You can try the Nouveau driver in the repository. Open source but an improvement over the Vesa driver. worth a try.

---

### Post by WitchCraft on 2010-04-04
> **MooPi said:**
> You can try the Nouveau driver in the repository. Open source but an improvement over the Vesa driver. worth a try.

[COLOR="Red"][SIZE="7"]**M**[/SIZE][/COLOR]esa, not Vesa.

Which driver would that be. There is no Nouveau driver in the repository.

---

### Post by MooPi on 2010-04-04
Excuse me on the mesa vesa. 
[http://packages.ubuntu.com/karmic/xserver-xorg-video-nouveau](http://packages.ubuntu.com/karmic/xserver-xorg-video-nouveau)

---

### Post by WitchCraft on 2010-04-04
[QUOTE=http://packages.ubuntu.com/karmic/xserver-xorg-video-nouveau]

Although the upstream nouveau drivers provide some 3D support, these packages do not include the necessary files. Users requiring 3D support should use the non-free "nvidia" driver.

[/QUOTE]

...

---

### Post by WitchCraft on 2010-04-05
Problem solved.


apt-get install xlibmesa-dri
apt-get install xlibmesa-gl
apt-get install xlibmesa-glu
apt-get install mesa-utils
apt-get install libgl1-mesa-dri
apt-get install libgl1-mesa-glx



zypper install freeglut libglue1
zypper install Mesa MesaGLw  Mesa-32bit
zypper install x11-video-nvidiaG02

---

### Post by WitchCraft on 2010-04-05
I take it back. Problem persists.
Thougn now I can work for 5 minutes until it crashes...

---

