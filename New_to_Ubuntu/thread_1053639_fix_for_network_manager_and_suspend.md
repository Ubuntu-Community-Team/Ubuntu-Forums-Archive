---
title: "fix for network manager and suspend?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-28
network manager refuses to connect after i wake from suspend and it's usually faster to restart my entire pc then try to reconnect.  is there and fix to this problem and don't say wicd because every time i restart my computer i can't even browse the web with wicd

---

### Post by Boomhauer on 2009-01-28
try ```
sudo /etc/init.d/networking restart
```

---

### Post by mamamia88 on 2009-01-28
well that worked and i got on quicker am i going to have to do that every time i suspend though?

---

### Post by Boomhauer on 2009-01-28
try this and if it doesnt work we will take it back out

go to a terminal and enter in ```
gksudo gedit /etc/default/acpi-support
``` and then look for the the part that says ```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""
``` and make it look like this ```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"
``` save and close the file then suspend/resume to see if it works.

---

### Post by mamamia88 on 2009-01-28
> **Boomhauer said:**
> try this and if it doesnt work we will take it back out

go to a terminal and enter in ```
gksudo gedit /etc/default/acpi-support
``` and then look for the the part that says ```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""
``` and make it look like this ```
# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="networking"
``` save and close the file then suspend/resume to see if it works.
 that seems to work thanks

---

