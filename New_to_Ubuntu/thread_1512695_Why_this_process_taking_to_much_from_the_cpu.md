---
title: "Why this process taking to much from the cpu ?"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-06-18
hello 

although my cpu speed is 1GH, but the system crashes and stuck from time to time, by open up system monitor i found that "gvfs-gdu-volume" process  taking the biggest chunk of my cpu usage  causing a lot of problems 

i need some help
picture is attached:

---

### Post by Chame_Wizard on 2010-06-18
[http://en.wikipedia.org/wiki/GVFS]("http://en.wikipedia.org/wiki/GVFS")
According to reports on Launchpad,it's mostly a bug.

---

### Post by cap10Ibraim on 2010-06-18
Would you like to kill it ?
try decreasing it's priority 
right click(on the process) -> change priority -> INCREASE the nice value

---

### Post by MBG1987 on 2010-06-18
> **cap10Ibraim said:**
> Would you like to kill it ?

i've killed it but it still existing after reopen system monitor!
also i set it to the lowest priority, still taking huge spce!
any more suggestions ?

---

