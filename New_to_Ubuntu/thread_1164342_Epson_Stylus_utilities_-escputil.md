---
title: "Epson Stylus utilities -escputil"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by john geary on 2009-05-19
I am new to linux and ubuntu so I am still confused as to where to find things.I have downloaded escputil for checking ink levels etc and it just seems to have disappeared,do I need something else to make it work and where do I find it?.I also downloaded mtink,when I tried to run it,it said That you have to join the Ip group,how do you do that?

---

### Post by Didius Falco on 2009-05-19
> **john geary said:**
> I am new to linux and ubuntu so I am still confused as to where to find things.I have downloaded escputil for checking ink levels etc and it just seems to have disappeared,do I need something else to make it work and where do I find it?.I also downloaded mtink,when I tried to run it,it said That you have to join the Ip group,how do you do that?

Welcome to the Ubuntu forums.

I can't help with the escputil, but I know where you can find out everything you need to know to get mtink working properly.

Read through this thread and you'll find all the info you need to set up mtink:

[http://ubuntuforums.org/showthread.php?t=1148178&highlight=mtink](http://ubuntuforums.org/showthread.php?t=1148178&highlight=mtink)

Regards,

Didius

P.S. It's the lowercase Lp group you need to join (lp) - instructions on how to do that are in the thread.

---

### Post by Mark Phelps on 2009-05-20
> **john geary said:**
> I also downloaded mtink,when I tried to run it,it said That you have to join the Ip group,how do you do that?
I use mtink all the time -- it's great. 

What you need to do is the following (presuming your user name is "username"):
1) Open a terminal
2) Enter the command "sudo useradd -G lp username"
3) Enter the command "sudo id username" to confirm that you got added to the lp group.

---

### Post by john geary on 2009-05-20
Mark and Didius,
Many thanks, i'm now firing on all six cylinders,it's a great program.:D

---

