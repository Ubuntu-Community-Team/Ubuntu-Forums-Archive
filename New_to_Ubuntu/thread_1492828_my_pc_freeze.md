---
title: "my pc freeze"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by muhammed.elkady on 2010-05-25
hello ;
 i have a big problem
i have a motherboard ( 945gct-m2/1333) and i use ubuntu 10.04 lts and my video card build in  

(00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)) 
my pc freezing after enabling 3d effects or compiz or fusion icon and i try a lot of solutions but no way to solve it
i have made all updates and no way 
please i need help . i am Beginner[
:confused::confused:

---

### Post by muhammed.elkady on 2010-05-25
hello ;
 i have a big problem
i have a motherboard ( 945gct-m2/1333) and i use ubuntu 10.04 lts and my  video card build in  

(00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ  Integrated Graphics Controller (rev 02)) 
my pc freezing after enabling 3d effects or compiz or fusion icon and i  try a lot of solutions but no way to solve it
i have made all updates and no way 
please i need help . i am Beginner:confused::confused::confused::confused:

---

### Post by cariboo on 2010-05-25
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by SRST Technologies on 2010-05-25
There's a number of ways to fix this problem of yours, but the two easiest for you are the following ways:

Don't use compiz and all that on such a crappy video adapter.

Buy a good video adapter and use that instead.

---

### Post by Babuloseo on 2010-05-25
My pc freezes or crashes( whats the difference between crash and freeze.. never though of it) whenever I run glxgears. Will have to test compiz, so i will get back to you!

---

### Post by muhammed.elkady on 2010-05-26
i will past this from the terminal
muhammed@muhammed-desktop:~$ wget [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download) -O compiz-check
--2010-05-26 10:54:54--  [http://blogage.de/files/9124/download](http://blogage.de/files/9124/download)
Resolving blogage.de... 188.40.53.170
Connecting to blogage.de|188.40.53.170|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 28360 (28K) [application/octet-stream]
Saving to: `compiz-check'

100%[======================================>] 28,360      49.8K/s   in 0.6s    

2010-05-26 10:54:56 (49.8 KB/s) - `compiz-check' saved [28360/28360]

muhammed@muhammed-desktop:~$ chmod +x compiz-check
muhammed@muhammed-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

