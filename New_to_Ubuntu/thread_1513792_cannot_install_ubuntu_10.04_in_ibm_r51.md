---
title: "cannot install ubuntu 10.04 in ibm r51"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by shashank.dommalapati on 2010-06-20
unable to install ubuntu 10.04 in my ibm r51 laptop

first i inserted the cd in the tray and selected inside windows the after finishing the installation when i rebooted , it a black screen appeared and continued for long time

i tried many other size of installations but it continued

before i used ubuntu 9.10 , it got installed successfully but this is not getting installed

---

### Post by overdrank on 2010-06-20
Hi and welcome, Moved to Absolute Beginner Talk

---

### Post by wilee-nilee on 2010-06-20
> **shashank.dommalapati said:**
> unable to install ubuntu 10.04 in my ibm r51 laptop

first i inserted the cd in the tray and selected inside windows the after finishing the installation when i rebooted , it a black screen appeared and continued for long time

i tried many other size of installations but it continued

before i used ubuntu 9.10 , it got installed successfully but this is not getting installed

Boot the live cd and post the script in my signature in code tags. Also in the live cd run this command and post it as well.
```
lspci | grep VGA
```

---

### Post by joejgarcia on 2010-06-29
Having the same problem here...  I am booting from the ubunbtu live cd to reload from scratch, no windows preinstalled.  Tried to disable acpi, etc but it always drops to a black screen and stops if I choose install or try out.  No console, no nothing, so I can't run the script.  Any other suggestions?

Joe

---

### Post by joejgarcia on 2010-06-29
Solved 

Hit f6 then escape, before the -- put in i915.modeset=1

Joe

---

