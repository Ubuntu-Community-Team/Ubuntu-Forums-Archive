---
title: "LCD brightness"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by stuckagain on 2009-12-04
Hi,
 
I have installed Xubuntu 9.10 on my IBM Thinkpad R40e. I am unable to adjust the brightness of the display. Can anyone tell me how to use the commands stated in the file /proc/acpi/ibm/brightness? The file contains the following -
 
level:  7
commands: up, down
commands: level <level> (<level> is 0-7)
 
I believe the commands are for controlling brightness level, but how and where do you issue them?
 
Rgds.

---

### Post by Excedio on 2009-12-04
I don't know how to do it what what you are asking to use, but have you tried using the brightness adjustment available in compiz?

---

### Post by stuckagain on 2009-12-04
Is compiz for Xubuntu? It will consume too much Ram i think, not for xfce.
 
Rgds.

---

### Post by Excedio on 2009-12-04
It seems to be available. Kind of an older blog post, but they have updated it all the way to 9.04.
 
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)

---

### Post by stuckagain on 2009-12-09
Solved the problem by turning acpi off. After setting the brightness level (with the usual keys), I turned acpi back on...
 
Rgds.

---

