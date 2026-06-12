---
title: "installing openGl"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by orky7 on 2010-02-11
i want to install openGl so i type in the command:
**sudo apt-get install libgl-dev libglu-dev**
and i get this output:


$ sudo apt-get install libgl-dev libglu-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libgl-dev is a virtual package provided by:
  libgl1-mesa-swx11-dev 7.4-0ubuntu3.2
  libgl1-mesa-dev 7.4-0ubuntu3.2
  nvidia-glx-96-dev 96.43.10-0ubuntu1
  nvidia-glx-71-dev 71.86.08-0ubuntu1
  nvidia-glx-180-dev 180.44-0ubuntu1
  nvidia-glx-173-dev 173.14.16-0ubuntu1
You should explicitly select one to install.
E: Package libgl-dev has no installation candidate

and i have a nvidia graphic ( with driver version 180.*.*) so what should i do use the mesa( then which one there are 2 options) one or the nvidia 180.* one or there is any alternate method to install. 
thanks...

---

### Post by Perfect Storm on 2010-02-11
It's
```
sudo apt-get install libgl1-mesa-dev
```

There's no package with the name libgl-dev

---

### Post by orky7 on 2010-02-11
thanks... but just out of curiosity are the mesa-dev and the nvidia-glx-dev are same in terms of functionality. i mean both is going to support the same standard openGl functions right??

---

### Post by Perfect Storm on 2010-02-11
Package Description:
> This version of Mesa provides GLX and DRI capabilities: it is capable of
both direct and indirect rendering.  For direct rendering, it can use DRI
modules from the libgl1-mesa-dri package to accelerate drawing.

This package does not include the OpenGL library itself, only the DRI
modules for accelerating direct rendering.

---

