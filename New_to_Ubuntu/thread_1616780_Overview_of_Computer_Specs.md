---
title: "Overview of Computer Specs?"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by WhatAreHackers on 2010-11-08
I'm using Ubuntu 10.10, I got a computer from my brother, i want to know my current specs, and i do not wish to take apart any of my computer parts.  What is my motherboard??  What is my power supply?  Any answer appreciated

---

### Post by sikander3786 on 2010-11-08
```
sudo lshw
```

will give you a detailed output.

---

### Post by kaldor on 2010-11-08
You can install the "hardinfo" application. Paste this command into the terminal: ```
sudo apt-get install hardinfo
```

Once installed, type "hardinfo" and it'll give you a graphical overview of everything.

---

