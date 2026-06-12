---
title: "Ubuntu Won't Relate To .py Files"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Ironman1 on 2009-05-05
I am making some basic Python scripts. I can run them in the IDLE but ubuntu won't recognize them as a file type.:confused:

---

### Post by cmnorton on 2009-05-05
Add this to the top file, after you enter which python to double-check.

#!/usr/bin/python

Also, protect file, so that at least you (and perhaps group?) can execute it
chmod 755 your-python-file.py

Then, entering 

./your-python-file.py

should do the trick.

---

### Post by Ironman1 on 2009-05-24
Thank You! :p

---

### Post by red_Marvin on 2009-05-24
If you want to change executability(eh) without touching other permission settings; chmod +x and chmod -x enables and disables the executable flags.

---

