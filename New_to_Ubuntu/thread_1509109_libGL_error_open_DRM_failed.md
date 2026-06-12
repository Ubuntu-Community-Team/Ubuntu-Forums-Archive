---
title: "libGL error: open DRM failed"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by asia1281 on 2010-06-13
I'm trying to ssh -X to my account on a server at school where I can run software that I'd like to be able to see the GUI for.  When I run the software I can't see the graphs or grids/meshes - anything that would be more graphics intensive.  It returns:

libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering

and apparently my direct rendering is turned off:

glxinfo | grep direct
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)

Some places online tell me to edit xorg.conf but others tell me I don't have to in Ubuntu 9.10.  [Others]("http://forums.heroesofnewerth.com/archive/index.php/t-61982.html") tell me Compiz is the culprit or that my video card is outdated and I am out of luck.  Running lspci returns this as my video card I think:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

Does anyone know if I'll be able to resolve this issue?  Thanks in advance for having a look.

---

