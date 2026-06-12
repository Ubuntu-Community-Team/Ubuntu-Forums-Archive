---
title: "Screenshots?!"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by Joshwaa on 2010-10-17
Okay, I can take screenshots, anyone can, there's a key for it..
BUT how do I edit them screenshots, like if I want to just crop out one bit of it? Which program should I use? Suggestions!

---

### Post by howefield on 2010-10-17
The included F-Spot Photo Manager can crop images, but for me, one of the first things I do when installing Ubuntu is install Gimp, so that's what I'd use. 

Bit of a sledgehammer for this particular nut, but works well.

---

### Post by sikander3786 on 2010-10-17
Krita, Kolourpaint, F-Spot, Gimp anything...

See these old threads for more suggestions.

[http://ubuntuforums.org/showthread.php?t=323480](http://ubuntuforums.org/showthread.php?t=323480)

[http://ubuntuforums.org/showthread.php?t=370493](http://ubuntuforums.org/showthread.php?t=370493)

---

### Post by fbobraga on 2010-10-17
I use **GIMP** (which is not instaled by default, but is ready to install in the "Software Centre"), but **Shotwell can do it**: just rightclick the generated file and choose "Open with" > "Shotwell"

---

### Post by Joshwaa on 2010-10-17
I have gimp but I stupidly installed GimpShop which makes Gimp (which I'm not used to) even harder to use, and I have to open it from the Terminal! Any suggestions how to remove Gimp and GimpShop?

---

### Post by howefield on 2010-10-17
Open System > Administration > Synaptic Package Manager and search for gimpshop, if it is there, mark for complete removal.

Alternatively, use the terminal command...

```
sudo apt-get purge gimpshop
``` 

Either way, keep an eye on what it wants to remove by way of dependancies. Just in case.

---

### Post by Joshwaa on 2010-10-17
> **howefield said:**
> Open System > Administration > Synaptic Package Manager and search for gimpshop, if it is there, mark for complete removal or use the terminal command...

```
sudo apt-get purge gimpshop
``` 

Either way, keep an eye on what it wants to remove by way of dependancies. Just in case.
Ah, cheers.
Btw what does Purge do?

---

### Post by howefield on 2010-10-17
> **Joshwaa said:**
> Ah, cheers.
Btw what does Purge do?

You could also use remove as in 

```
sudo apt-get remove gimpshop
```

The difference being that remove just uninstalls the binaries whereas purge also removes the config files.

---

### Post by Joshwaa on 2010-10-17
> **howefield said:**
> You could also use remove as in 

```
sudo apt-get remove gimpshop
```

The difference being that remove just uninstalls the binaries whereas purge also removes the config files.
Ah, thanks :).

---

