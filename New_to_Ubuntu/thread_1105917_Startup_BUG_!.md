---
title: "Startup BUG ?!"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by 4JOKE on 2009-03-25
I have installed vncserver and when I start it by command **vncserver**, It makes **one** remote desktop.

So I tryed to put command **vncserver** to **Autostarted Apps** to start one vncserver every time when I turn on pc.

But there is a **problem**. It always start **22x vncserver** ?! Why ?!

Here is my screenshot:
[IMG]http://obrazok.eu/files/8z975hpde0yrneuo4d1e.jpg[/IMG]


**//EDIT:**
I find out also, that everything is run so many times... ?!?!?!
I now try to explain exactly what I done:
- start new installation of Xubuntu 8.10
- then I downloaded/installed all updates from internet
- then installed graphic card driver which Xubuntu recommended to me  to install it
- after that I installed vncserver and put it into Autostarted Apps.
That's everything.

[IMG]http://obrazok.eu/files/flgd80j3ch1gpelc069u.jpg[/IMG]

---

### Post by cariboo on 2009-03-25
It looks like you have your desktop set to save the state it was in when you shutdown, from your screenshot the autostartup dialog says that it will restart with the saved state of your desktop.

If you manage to close all the extra vnc instances, what happens when you start vnc manually?

Jim

---

### Post by 4JOKE on 2009-03-25
When I closed all xvnc processes in System Monitor and run command **vncserver** in terminal again, it started making many vncservers again...

---

### Post by 4JOKE on 2009-03-26
I made some tests.

1) When vncserver command IS in Autostarted Apps:
- xubuntu starts with many vncservers and also I can see in System Monitor, that other tasts are run many times too.
- when I close all vncservers, then other tasks are automatically cancelled too.
- after that when I run command vncserver in terminal, everything starts to run many times again.

2) When vncserver command IS NOT in Autostarted Apps:
- xubuntu starts normally and other tasks are running one time.
- when I run command vncserver in terminal, It will run only one vncserver but some tasks are run 2times.

...what's wrong with my clear installation of xubuntu ?!

---

