---
title: "loading the script at boot"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by anirudhmalpe on 2010-08-27
I have created a script which is displayed below to lock the terminal with a password protection.I copied the following shell script to the init.d folder and executed the command "update -rc.d filename defaults" to load the script to the system but it shows me a error saying that my script does'nt satisfy the specifications.so please help me by adding the specifications for the following script and please tell me if I am doing this in a wrong way.



#!/bin/bash

stty -echo

while [ "$m" != "password" ]

do

clear

echo  "\nkeyboard  locked"

echo  "\nenter the same password to unlock:\c"

read m

done

clear

echo  "keyboard unlocked"

stty echo



please help me with the specifications since i'm a beginner in this can you please add the specifications compatible for init.d for the above program.

---

### Post by Daniel0108 on 2010-08-27
Hi!
I made a script, which starts on shutdown...
I had the same error, but the script worked, though :P
So, just try it, and see if the script executes ;)
Yours,
Daniel

---

### Post by anirudhmalpe on 2010-08-27
Hi daniel
the script works fine but it does'nt load during the boot so if you get to know a way please let me know.
thank you:-)

---

