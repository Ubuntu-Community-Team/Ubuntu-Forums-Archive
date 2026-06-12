---
title: "kernel panic not syncing vfs unable to mount root fs on unknown block (8,3)"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by zeyacry on 2009-11-08
hi,

I am new to linux platform and i installed ubuntu 9.10 using wubi in another partition. I got this error message" [0.986310] kernel panic -not syncing vfs unable to mount fs on unknown block (8.3)". I saw this message after doing a complete removal of the following packages using synaptic package manager. I'm removing the java packages because the errors occurred during installation.

sun-java6-bin

 sun-java6-demo

 sun-java6-doc

 sun-java6-fonts
  sun-java6-jre

 sun-java6-plugin

 sun-java6-source

I would hope that i can still log in to the desktop to extract my files for my work. Hope someone can help me in overcoming this problem.

---

### Post by MelDJ on 2009-11-08
try this thread: [http://ubuntuforums.org/showthread.php?t=1314058](http://ubuntuforums.org/showthread.php?t=1314058)

---

### Post by zeyacry on 2009-11-09
> **MelDJ said:**
> try this thread: [http://ubuntuforums.org/showthread.php?t=1314058](http://ubuntuforums.org/showthread.php?t=1314058)

Hi, 
Thanks for your prompt reply. 

I'm reading the thread that you quoted. I can't boot in recovery mode either. Does it mean that i cannot fsck my drive? 

Then mentioning about the part on "defrag of the /wubi folder". Does it mean defrag the drive in window environment? I don't understand which /wubi folder that it is mentioning.

Please enlighten me!

---

### Post by MelDJ on 2009-11-09
i believe you have to defrag the disk where wubi is.
i got impatient and just removed it though:p

---

### Post by zeyacry on 2009-11-09
> **MelDJ said:**
> i believe you have to defrag the disk where wubi is.
i got impatient and just removed it though:p
Wow! you amazed me! 

Anyway, i'm still doing disk check for my whole drive. i guess maybe because i move the wubi folder to recycle bin after the installation. 

I'll try it out! :)

---

### Post by MelDJ on 2009-11-09
> **zeyacry said:**
> Wow! you amazed me! 

Anyway, i'm still doing disk check for my whole drive. i guess maybe because i move the wubi folder to recycle bin after the installation. 

I'll try it out! :)

is laziness amazing? :D

---

### Post by catco_designs on 2009-11-09
you can defrag it or uninstall and try another method like dualboot boot from livecd

---

### Post by zeyacry on 2009-11-13
hi palz!!,

Thanks for giving me so much advices! i finally decided to uninstall wubi from my computer.. Then it surprised me when i found my files (which is placed in ubuntu) in this directory (C:\.Trash-1000\files). 

I'll dual boot ubuntu next time round and be more careful with my impt files!!

zeyacry

---

