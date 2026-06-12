---
title: "terminal commands @ startup"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by nobodygh on 2009-09-22
Is there any way in which I can get certain terminal commands to run when Ubuntu starts up?

I want to run fortune (or maybe fortune | cowsay) then I will have something like a custom greeting message \\:D/

---

### Post by dje on 2009-09-22
Try this
```
zenity --info --title "Welcome" --text "$(fortune)"
```
See
```
man zenity
```
for other options ;)

to run at startup create a text file (script) with the following content:
```
#!/bin/bash

zenity --info --title "Welcome" --text "$(fortune)"
```
then run:
```
chmod +x */path/to/script*
```
then add the path to System >> Preferences >> Startup Applications

dje

---

