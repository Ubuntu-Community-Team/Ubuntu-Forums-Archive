---
title: "U-lite runs the cpu full"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by PLANETARY on 2009-01-24
I installed U-lite, installed ndiswrapper, rebooted, bottom panel was gone, made a new one. my cpu run at 100% even when its 'idling'. What is it doing? There is no task manager so I dont know what its  doing. Its cooking my 800mhz P3 512ram laptop.

Help please, so far its pretty cool.

It happens when I right click on the desktop. Initially it is a blank blue background then when i right click it has a lxde menu. Tho when I start PCMAN file manager it freaks out. the desktop icons come back and the cpu runs its *** off. 
I tried unistalling pcman file manager and install pcmannohal, didnt  work. 

It doesnt always start pcman at start up but so i right click and select pcman and my desktop looks normal with icons. I can run pcman and view fils and folders however if i right click on the desktop it goes nuts. 

I think this thread should be moved to the desktop environment section

---

### Post by emarkd on 2009-01-24
you can use the 'top' command from the terminal to see what's using the cpu.

alternatively, you can use the widget at system > administration > system monitor

---

### Post by PLANETARY on 2009-01-25
oh good I didnt know about the top command. system monitor isnt on there. Lxde is installed on a base ubuntu. 

Top says its pcmanfm causeing the problem. I tried to kill it but I must have not done it right. 

anywho any thoughs?

---

### Post by jrusso2 on 2009-01-25
uninstall pcmanFM if its causing all those problems.  It must be buggy.

---

