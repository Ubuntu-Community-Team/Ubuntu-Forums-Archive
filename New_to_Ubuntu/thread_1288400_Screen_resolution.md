---
title: "Screen resolution"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by Gazzaz on 2009-10-11
The screen resolution is too big.
Dimension is 640*480 pixels
how can make it normal.

VGA card Ge Force  fx5200

---

### Post by Nevart on 2009-10-11
On the Launch Panel (the one that has "Applications, Places, System" etc) you will see a little icon that looks like a monitor with a triangular set-square on the corner of it.  Click on that and it gives you a dialog where you can change the screen resolution to whatever your monitor and video card will support.

---

### Post by Gazzaz on 2009-10-11
i tried it but it says that" It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"
then i pressed no
another window appeared to configure screen
and i changed 640*480 into 1024*786
but it says that it cant configure crtc 398
please help

---

### Post by Bölvaður on 2009-10-11
*added*
according to your last post it appears you may already have done the grayed out part. Continue further down.
Btw you should have pressed YES when prompted.
[COLOR="Silver"]
Look at your top panel
***System &#8594; Administration &#8594; Hardware Drivers***
select a driver named something similar to 173.14.20 (this is the newest driver but an older more stable driver is available under *Hardware Drivers*)


After installing you need to use it, which is already linked to the kernel. This is the only reason you will ever need to restart. So restart now for the driver to take effect.
[/COLOR]
Go to ***System &#8594; Administration &#8594; NVIDIA X Server Settings***
(if it doesnt ask you for password please press alt+f2 and type "gksu nvidia-settings", this is for permission to store the changes you will make)


***X Server Display Configuration***
*Resolution*: what ever you want.
Press *Save to X configuration file*

---

### Post by Gazzaz on 2009-10-11
i tried that too,
not workin
coz it has only 640*480,320*240 and auto resolution as default  
help

---

### Post by wojox on 2009-10-11
What nvidia driver version is loaded ? Also what type monitor do you have ?

```
lspci | grep VGA
```

---

### Post by Gazzaz on 2009-10-11
its  nvidia geforce fx 5200
crt monitor 
1024*786 was the resolution when i was using win 7

---

### Post by Gazzaz on 2009-10-11
i have downloaded nvidia driver NVIDIA-Linux-x86-173.14.20-pkg1
what am i supposed to do now

---

### Post by houstonbofh on 2009-10-11
Start by not installing the package.  Go  into Hardware Drivers, and see what is installed (If anything)  As the 5200 is not exactly cutting edge, I think you will need an older driver, and Hardware Drivers can give you some hints.

---

### Post by wojox on 2009-10-11
> **Gazzaz said:**
> i have downloaded nvidia driver NVIDIA-Linux-x86-173.14.20-pkg1
what am i supposed to do now

Downloaded from where, the nvidia site or synaptic?

Never mind I see it's .20. That's the same driver I use. I upgraded with the help of this HowTo: [http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400)

---

