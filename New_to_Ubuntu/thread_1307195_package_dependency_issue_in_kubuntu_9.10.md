---
title: "package dependency issue in kubuntu 9.10"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by RyanBones on 2009-10-30
p, li { white-space: pre-wrap; }  Hello everyone, been experincing a rather unusal issue. it was orginally working after I updated but appears not to be now.



A package dependency could not be found.
 More information is available in the detailed report.


detailed report: 

there are broken dependencies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this issue.




what exactly should I do or go about doing to resolve this?

---

### Post by sandyd on 2009-10-30
> **RyanBones said:**
> p, li { white-space: pre-wrap; }  Hello everyone, been experincing a rather unusal issue. it was orginally working after I updated but appears not to be now.



A package dependency could not be found.
 More information is available in the detailed report.


detailed report: 

there are broken dependencies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this issue.




what exactly should I do or go about doing to resolve this?
open synaptic and install the package from there.
kpackagekit (i assume thats what your using) is quite broken these days....

---

### Post by Buuntu on 2009-10-30
Yes use synaptic, but to fix broken dependencies that you may have already you can run
```
sudo apt-get install -f
```

---

### Post by Xatolos on 2009-10-30
Also to see the broken package dependancys go to System -> Administration -> Synaptic Package Manager.
From there click on Custom Filters and the list above highlight Broken.
Can delete and re-install from there

---

### Post by dubs65401 on 2009-11-15
> **Buuntu said:**
> Yes use synaptic, but to fix broken dependencies that you may have already you can run
```
sudo apt-get install -f
```
Thank you you save me a big head ach you are good  i am hoping you can help me with this kttsd faild message i am having. i install kttsd and i still have the message help.

---

### Post by Buuntu on 2009-11-17
You are very welcome :D.  Try running this in the terminal to fix kttsd:
```
sudo apt-get purge kttsd && sudo apt-get install kttsd
```
'sudo apt-get purge kttsd' will completely remove kttsd and all its config files from your system and 'sudo apt-get install kttsd' simply reinstalls it.  I don't know if this is the problem, but it's definitely worth a try.

---

### Post by daniel4999 on 2010-12-19
thnx man!:D

---

