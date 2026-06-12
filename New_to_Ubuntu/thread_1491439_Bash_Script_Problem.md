---
title: "Bash Script Problem"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-23
when i execute a hello world bash file, terminal appears and disappears, nothing else happens.
what to do now in order to see the resulted "hello world" text?

---

### Post by sharath.puranik on 2010-05-23
Show us the code you are using for this script.

---

### Post by da burger on 2010-05-23
If a terminal is opened by a launcher it closes again when the program finishes. Try running the command from with a terminal.

---

### Post by tada on 2010-05-23
Add the following to the end of your script:

read x


This will force the code to wait for you to hit enter - so if this is being shown in a popup terminal, that terminal will have to wait for you.

X is nothing important - its the 'read' thats doing the work

---

### Post by lovinglinux on 2010-05-23
Open the terminal, go to "Edit >> Profile Preferences >> Title and Command >> "When command exits" and set it to "Hold the terminal open".

You could also add a command to the end of script to keep it open, but I'm trying to figure out which command would do that myself.

Edit: the command is on previous post :)

---

### Post by bumanie on 2010-05-23
[Here's a good]("http://gd.tuwien.ac.at/linuxcommand.org/writing_shell_scripts.php") (and easy to follow) tutorial on bash script writing. Hope it helps.

---

### Post by SKhan on 2010-05-24
> **sharath.puranik said:**
> Show us the code you are using for this script.
```
#! /bin/bash
echo "Hello World!"
```

---

### Post by SKhan on 2010-05-24
thanks guys problem solved.

---

