---
title: "Why nautlis taking too much to respond??!!"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-07-19
When i attempt to open a directory using nautlis it takes too much time "sometimes 20 second or more!!" to show it's contents, Trash for instance although it contains a few mb of files.

ubuntu 9.10
nautlis 2.28.1
kernel version 2.6.31-14-generic
RAM 1 GB
CPU 2.20GHz dual core 

any help?

---

### Post by Paqman on 2010-07-19
Couple of things you could try:

[LIST=1]
[*]Open a terminal and type: nautilus, it might produce some useful output.
[*]Create a new account and see if you get the same problem.
[/LIST]

---

### Post by MBG1987 on 2010-07-19
> **Paqman said:**
> 
[LIST=1]
[*]Open a terminal and type: nautilus, it might produce some useful output.
[/LIST]

  
i got :

[PHP]$ nautilus

(nautilus:3451): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
[/PHP]

---

