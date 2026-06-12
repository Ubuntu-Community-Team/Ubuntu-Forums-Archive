---
title: "getting an icon on the desktop"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by Room533 on 2009-05-24
Hi.  I have an installed application that I can't figure out how to run. Synaptic says it's there. But i can't find the executable file (is that .bin or .sh or ?).  Thanks for any light you can shine.

---

### Post by Tibuda on 2009-05-24
Most Linux executables don't have an extension, and are installed under /usr/bin or /bin.

---

### Post by Uzi304 on 2009-05-24
If you've installed it through Synaptic, it should be in /usr/bin

---

### Post by drs305 on 2009-05-24
If you can see it in Synaptic, you can right click, Properties, installed files and see what the executable is. As was stated, usually it's in /usr/bin.

You can also type the following in terminal to find the information:
```

which *appname* # provides the run command. Example: which gimp
whereis *appname* # provides the file locations  Example: whereis gimp

```

---

### Post by Viva on 2009-05-24
Depends on what you've installed.

---

