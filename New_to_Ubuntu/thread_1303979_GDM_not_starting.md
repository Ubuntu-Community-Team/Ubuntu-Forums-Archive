---
title: "GDM not starting"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Poincare101 on 2009-10-28
I have been using ubuntu like this since day 1. The thing is, if I leave the screen unfolded (its a laptop) for a while (say 10 mins) gdm basically freezes. All that shows up is a black screen and nothing happens when I move the mouse. I have to crash it, start it up again. Again, the same thing happens. Then, I crash it and start it up again and it works. What should I do to fix this? 

(I've already done recovery mode and fix x11 and all that)

---

### Post by sandyd on 2009-10-28
> **Poincare101 said:**
> I have been using ubuntu like this since day 1. The thing is, if I leave the screen unfolded (its a laptop) for a while (say 10 mins) gdm basically freezes. All that shows up is a black screen and nothing happens when I move the mouse. I have to crash it, start it up again. Again, the same thing happens. Then, I crash it and start it up again and it works. What should I do to fix this? 

(I've already done recovery mode and fix x11 and all that)
have you installed your video drivers?

---

### Post by Poincare101 on 2009-10-28
How would I do that?

---

### Post by sandyd on 2009-10-28
System -> Administration -> Hardware Drivers.

---

### Post by Poincare101 on 2009-10-31
It says:
No proprietary drivers in use on this system.

---

### Post by Poincare101 on 2009-10-31
anyone?

---

### Post by cariboo on 2009-10-31
If you have an /etc/X11/xorg.conf file move it to a backup, and start without it. Open a terminal and type:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then restart. The drivers should show up in System-->Administration-->Hardware Drivers. I have the same graphics adapter, notification of restricted drivers are available even show up using Live CD.

---

### Post by Poincare101 on 2009-10-31
Still says the same thing.

---

### Post by cariboo on 2009-10-31
If for some reason your graphics adapter is not being detected properly you may have to manually install the drivers. Go to System-->Administration-->Synaptic Package Manager and search for **nvidia-glx-185**, and mark it for installation. Once the installation is finished, you may have to open a terminal and type:

```
nvidia-xconfig
```

---

### Post by emigrant on 2009-10-31
[Poincare101]("http://ubuntuforums.org/member.php?u=795531"), disable the screensaver if you have any.

---

### Post by Poincare101 on 2009-10-31
> **cariboo907 said:**
> If for some reason your graphics adapter is not being detected properly you may have to manually install the drivers. Go to System-->Administration-->Synaptic Package Manager and search for **nvidia-glx-185**, and mark it for installation. Once the installation is finished, you may have to open a terminal and type:

```
nvidia-xconfig
```

I can't find nvidia-glx-185, however, I can find nvidia-glx-180

---

### Post by sandyd on 2009-10-31
> **Poincare101 said:**
> Still says the same thing.
have you tried downloading the drivers from the ati/nvidia site manually?

---

### Post by sandyd on 2009-10-31
> **Poincare101 said:**
> I can't find nvidia-glx-185, however, I can find nvidia-glx-180
then use nvidia-glx-180.

---

