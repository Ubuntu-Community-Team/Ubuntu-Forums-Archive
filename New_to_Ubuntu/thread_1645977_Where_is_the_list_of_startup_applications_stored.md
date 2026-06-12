---
title: "Where is the list of startup applications stored?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by awp2513_ on 2010-12-15
Hi,

I'm using Ubuntu 10.04 netbook remix and I'm trying to find out where the list of startup applications is stored (gconf, ~/.config/, etc.), but I haven't had any luck.

Some people recommended ~/.config/autostart, but that doesn't exist on my system. I've done multiple greps and searches in gconf, but I'm probably searching for the wrong thing.

My goal is to be able to add another startup program from a script (so using the menu won't be an option). Is there a specific file or gconf key that I can modify in order to accomplish this?

Thanks in advance

---

### Post by NCLI on 2010-12-15
Can't you just enter the location of your script in the Startup Applications manager?

---

### Post by awp2513_ on 2010-12-15
Hi,

Sorry, maybe I wasn't specific enough.

I'm writing a script that will set the system up the way I want. Among other things, I need to add another application to the list of startup applications from this script, which means I cannot user System->Startup Applications (the menu).

---

### Post by CowzRule on 2010-12-15
Have a look in the folder "/etc/xdg/autostart"

---

