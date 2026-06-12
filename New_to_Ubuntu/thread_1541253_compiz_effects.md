---
title: "compiz effects"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by Messyhair42 on 2010-07-28
after I restarted all my window borders were missing (close, minimize), i turned off all compiz effects and no difference. this happens every time i upgrade and it's always the most frustrating thing to do. any help would be appreciated.

---

### Post by 23dornot23d on 2010-07-28
What are you running .... which version ...... do this in a terminal and post the result. 

uname -a

What graphics card too ..... is it a (Nvidia or other) .... and if so which one .... ?

---

### Post by Ast_risk on 2010-07-28
> **Messyhair42 said:**
> after I restarted all my window borders were missing (close, minimize), i turned off all compiz effects and no difference. this happens every time i upgrade and it's always the most frustrating thing to do. any help would be appreciated.
Do you mean the window borders? If so, there should be an option to enable window borders in the CompizConfig Settings Manager.

---

### Post by Messyhair42 on 2010-07-28
Linux deepthought 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

i just did the upgrade to the latest kernel verion. and if it wasn't clear before, everything was working before i rebooted and it's not the same afterwards. i have an GeForce 7200 GS video card, running the most current NVIDIA driver

and "window borders" itself doesn't appear in CompizConfig Settings Manage.

---

### Post by 23dornot23d on 2010-07-29
Can you still boot into the old kernel ..... does it work ok if you do ?

do you have an xorg.conf

etc/X11/xorg.conf

Check 
System - Administration
hardware drivers and Nvidia-server-settings

Post screenshots if you can ..... just check and see if the driver is loaded up.

For some reason the Nvidia Drivers do not always load when the new kernel is added.
The kernel headers need to be there - if not the graphics do not seem to work properly.
might be worth checking in synaptic and making sure the headers are there too.

---

### Post by nigelreloaded on 2010-07-29
this also happened to me but im using a radeon card

i tried to reinstall the driver and it did all the job

---

### Post by rvgsd on 2010-07-29
Just wondering if you have a window manager, when you start compiz. I had that problem, which got solved after I installed Emerald.

---

### Post by 23dornot23d on 2010-07-29
There seems to be a Bug raised ..... this is the thread I originally saw ... 
the bug may be slightly different as its for customized kernels

The solution to that for one person was to purge the package and then to [re-install nvidia-common]("http://ubuntuforums.org/showthread.php?t=1539035")
My thoughts on initially seeing the problem are to do with the (*Nvidia) graphics driver not loading .....
as similar has happened to mine in the past.

---

### Post by Messyhair42 on 2010-07-30
so I booted to 2.6.32.23 and everything is working fine
compiz isn't a window manger? i thought it was
xorg.conf exists and i'm running "version current" of the Nvidia driver

---

