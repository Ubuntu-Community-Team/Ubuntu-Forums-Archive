---
title: "How to change default video resolution"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by coldfinger on 2010-06-19
I've learned how to change my video resolution by using the xrandr command.  I want to change my default resolution, so that I don't have to manually change it each time I log in. 

Assuming that I would need to make an entry in xorg.conf, what should that entry be, and in which directory should it be stored?


Thanks,
Coldfinger

---

### Post by freddiespagheti on 2010-06-19
Hmm... I don't really like editing xorg.conf myself so this might not be the answer you're looking for but you could try a bash script and have it executed at startup. Open a text file and enter:

```
#! /bin/bash

*put command here*
```

save it as screen.sh or something to your liking and make it executable. (Right click, properties, permissions or something like that)

Then just place it somewhere you won't lose it and add it to startup.

It probably would be better just to edit xorg.conf but I always get confused when I look into that.

---

### Post by coldfinger on 2010-06-19
Freddie S:  I'll try creating a bash script.  Forgive my ignorance, but how do I add it to startup?
 
Thanks,
Coldfinger

---

### Post by Windows Nerd on 2010-06-19
> **coldfinger said:**
> Freddie S:  I'll try creating a bash script.  Forgive my ignorance, but how do I add it to startup?
 
Thanks,
Coldfinger
GNOME Menu>System>Preferences>Startup Applications. Hit add. It will popup a Dialogue box. Set the name as something like "Set Screen Resolution" or anything you like. As for the command, hit browse and find your script. Set the description to anything you like. Hit Add. 

This should run the script at startup. Reply if you have any questions. 

Scott

---

### Post by coldfinger on 2010-06-20
This works well!  Thanks guys.

---

