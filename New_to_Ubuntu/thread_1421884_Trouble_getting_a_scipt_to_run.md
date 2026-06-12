---
title: "Trouble getting a scipt to run"
date: 2010-03-04
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-03-04
When I try to run a simple rsync script, a terminal window pops up in the taskbar for a split second and then closes but the script never runs.  It's only one command long, and I tested the code and it works if I input it manually into the terminal.  I also have changed the script to executable.   Any ideas??

---

### Post by baddnady23 on 2010-03-04
Here is the script...

```
#!bin/bash

rsync -av --delete --log-file=/home/andrew/Desktop/$(date +%Y%m%d)_rsync.log /home/andrew/Documents /home/andrew/Test
```

---

### Post by alarme on 2010-03-04
Hi, you lost a slash after the shebang

Try:

#!/bin/bash

also, be sure you gave it execution bits

chmod +x your_script_name_here

if you don't have set execution bits, you can run it writing:

sh /path_to_file/your_script_name_here

but not double clicking in Nautilus

regards

---

### Post by baddnady23 on 2010-03-04
Silly me. Funny how something as little as that throws it off like that.  Thank you

---

