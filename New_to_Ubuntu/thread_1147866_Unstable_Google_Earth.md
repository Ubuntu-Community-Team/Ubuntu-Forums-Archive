---
title: "Unstable Google Earth"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by harecanada on 2009-05-03
I installed Google Earth but it flashes and acts weird and unstable.
Is there any way to stableize it?
harecanada

---

### Post by tjwoosta on 2009-05-03
disable compiz

its not just google earth, its anything that uses opengl rendering


easy way is to do this before using it
```
metacity --replace
```

then do this after your done with it
```
compiz --replace
```


or the even easier way, you could make a simple script to start google earth with

(paste this into a text editor and save as googleearth.sh then make it executable)

```

#!/bin/sh

metacity --replace &

googleearth

compiz --replace &

```

then you can just make a launcher and/or change the menu entry to run /path/to/file/googleearth.sh

---

