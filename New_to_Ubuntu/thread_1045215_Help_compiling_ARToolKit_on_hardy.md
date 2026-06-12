---
title: "Help compiling ARToolKit on hardy"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by arikshtiv on 2009-01-20
I am trying to compile ARToolkit with 'make', but I get these errors:
```
gsub_lite.c:649: error: conflicting types for ‘arglCameraFrustum’
../../../include/AR/gsub_lite.h:258: error: previous declaration of ‘arglCameraFrustum’ was here
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:656: error: request for member ‘xsize’ in something not a structure or union
gsub_lite.c:657: error: request for member ‘ysize’ in something not a structure or union
gsub_lite.c:659: error: request for member ‘mat’ in something not a structure or union
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type

```

can anyone help?
thanks in advance.

---

### Post by arikshtiv on 2009-01-22
*BUMP*

anyone?

---

