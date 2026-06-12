---
title: "g++ and Xext"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by gdoermann on 2011-04-01
I am trying to build Qt from sources and I keep getting an error in the make saying ld can't find Xext (-lXext).  I remove that option and it builds that section just fine... what would that do?  I installed x11proto-xext-dev, but that didn't make a difference.  Anyone know why I would be getting that error?

---

### Post by gmargo on 2011-04-01
You need to install the **libxext-dev** package to link with -lXext.

---

### Post by gdoermann on 2011-04-01
Thanks! That worked!

---

