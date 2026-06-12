---
title: "How do I launch a program on a seperate x screen?"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by klemperal on 2009-01-18
Alright, I have my computer hooked up to my regular monitor and tv which are set as separate x screens.  Besides using xinerama to drag stuff over to my tv screen is there a way to launch specific programs directly to my tv screen?

---

### Post by mjheagle8 on 2009-01-18
you cant set a program to open on a different workspace or screen to the best of my knowledge.

---

### Post by klemperal on 2009-01-18
How about for one instance.  It seems like there should be a way via command line.

---

### Post by mjheagle8 on 2009-01-18
the only way i can think of would be to have the program set its own x properties. i think you'd have to edit the program source.

---

### Post by klemperal on 2009-01-18
Dang.  Thats pretty disheartening seeing as its not hard to do in Windows.

---

### Post by aesis05401 on 2009-01-18
[http://ubuntuforums.org/showthread.php?t=844385]("http://ubuntuforums.org/showthread.php?t=844385")

Is this what you are looking for?  


* Note the Compiz tip.. I haven't used these but that was where I would start looking FWIW.

---

### Post by amauk on 2009-01-18
you can do this by specifying the DISPLAY var

open up one terminal on each x-screen, and type in
```
echo "$DISPLAY"
```
this will give you the screen numbers of each screen
(Eg. mine are :0.0 & :0.1)

open up a terminal on screen :0.0
and type in
```
export DISPLAY=:0.1 && nautilus
```
Nautilus will now open on the other screen

If you want certain apps to load on certain screens, just edit the command in the menus (or desktop icon) to set the DISPLAY var

---

### Post by aesis05401 on 2009-01-18
> **amauk said:**
> If you want certain apps to load on certain screens, just edit the command in the menus (or desktop icon) to set the DISPLAY var


Sweet.

---

### Post by klemperal on 2009-01-18
> **amauk said:**
> If you want certain apps to load on certain screens, just edit the command in the menus (or desktop icon) to set the DISPLAY var

Ok, it says my tv screen is 0:1.  The command for the program I want to run on screen 0:1 is  ```
/opt/boxee/run-boxee-desktop
```  What exactly do I add to this line to make it go to screen 0:1?

---

### Post by amauk on 2009-01-18
> **klemperal said:**
> Ok, it says my tv screen is 0:1.  The command for the program I want to run on screen 0:1 is  ```
/opt/boxee/run-boxee-desktop
```  What exactly do I add to this line to make it go to screen 0:1?
I personally have a custom launcher folder in my home folder

~/.launchers/

inside that, I have scripts for modifying program behaviour

inside your launchers folder, make a file called "boxee-desktop"

open boxee-desktop, and write
```
#! /bin/sh

# Run boxee on screen :0.1
export DISPLAY=:0.1
/opt/boxee/run-boxee-desktop
```

make file executable (in properties)

then edit your icon or menu entry
in "command", use "~/.launchers/boxee-desktop"

---

### Post by klemperal on 2009-01-18
Very cool.  Thanks so much for the help.

---

