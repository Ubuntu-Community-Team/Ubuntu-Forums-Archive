---
title: "Problem with conky"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by sadaruwan12 on 2009-06-30
I've managed to get my conky customized and running but the problem I face is that when I put conky to auto run from the boot it starts up and runs behind my wallpaper but when I run it manually from the terminal it runs and displays itself on my wallpaper. Now don't tell me to get ride of my wallpaper 'cos I love my wallpaper. So I would like to know if any one managed to get conky to run automatically from the startup on the desktop with out removing the wallpaper.

ThX in advance

---

### Post by sadaruwan12 on 2009-06-30
Plz can any one help me

---

### Post by TeoBigusGeekus on 2009-06-30
You have a startup script for conky. Add a line to make it start with a delay, i.e. modify your startup script like this:
```
sleep 10
conky
```
It is a common conky bug.
Post us if you have any success.

---

### Post by VCoolio on 2009-06-30
too slow, TBG beat me :P

---

### Post by sadaruwan12 on 2009-06-30
THX it worked ! I created an .sh file (.conky_start.sh) inserted the the below code in to it

```
#!/bin/bash
sleep 15 && conky;
```

and changed the permissions using

```
sudo chmod a+x .conky_start.sh
```

now it works

---

