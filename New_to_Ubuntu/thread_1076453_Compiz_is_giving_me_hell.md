---
title: "Compiz is giving me hell"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by optional on 2009-02-21
Hello everybody.

When I activated compiz earlier today it just gave me a blank white cube and nothing else. I can rotate the cube but it's just white...
I tried to restart and it begins normally, showing the login screen and then begins by showing the desktop but then just goes back to that white cube...
What can I do to shut down compiz?

---

### Post by taurus on 2009-02-21
System -> Preferences -> Appearance -> Visual Effects -> _N_one.

---

### Post by optional on 2009-02-21
The thing is that I cant do anything using the graphical interface.
Do you know how to do this in command line mode?

---

### Post by philinux on 2009-02-21
```
metacity --replace
```

---

### Post by Sealbhach on 2009-02-21
Maybe you don't have enough memory to run Compiz?


.

---

### Post by optional on 2009-02-21
Thanks for your answers, the problem somehow went away with the 4th restart.
Don't think I will be using compiz much in the future though..

---

### Post by optional on 2009-02-21
I have 4 GB RAM so I think I have enough memory :)

---

### Post by Blåbär on 2009-02-23
Hey guys.

I didn't see it necessary to start a new thread, so I'll just give it a go from here...

I've tried out conky some, but then a friend told me about compiz and it looked way more.. alluring if you will. The problem is that when I run compiz I get this:

```
~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: present. 
Software rasterizer detected, abortingaborting and using fallback: /usr/bin/metacity
```

A window seem to flash by, closing faster than it opens.

I'm running on 8.10 (64bits), 4GB ram. No other applications were running while I did the above.

Any help will be appreciated.
Thanks,
Blabar

---

