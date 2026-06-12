---
title: "restricted nvidia drivers borked me"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by mbgb14 on 2009-01-22
Hey gang,

I installed a fresh copy of Xubuntu onto my machine with an Nvidia card in it. The screen resolution is huge and completely wrong for the size of monitor. So naturally, I clicked to install the restricted drivers. Installed properly, rebooted - thought all would work flawlessly. Wrong.

It somehow borked my entire xorg.conf, making graphical desktop completely imoperable. So I copied the borked version to a backup, and then removed the xorg.conf altogether. Upon restarting gdm, it figured out there was no xorg to be found, so it somehow spawned me back to the way I had it at the start - the wrong resolution. I removed the driver using the restricted driver tool, and for now I'm at 800x600.


Question

1) I have no xorg.conf. At all. I need to make a change to it for something else irrelevant to this conversation. But I have none.

2) How do I get my proper display drivers up and running, so I'm not stuck with this 800x600 stuff?


If someone can point me in the right direction, that'd be great. Tx.

--------------------

FIXED WITH THIS THREAD:
[http://ubuntuforums.org/showthread.php?t=965180&highlight=nvidia+gui](http://ubuntuforums.org/showthread.php?t=965180&highlight=nvidia+gui)

---

### Post by Stalker72 on 2009-01-22
Did you activate version 173 or 177?

Have you tried booting into recovery mode? From there, you could try to fix X server, etc.

Stalker72

---

### Post by mbgb14 on 2009-01-22
The latest one. 

I fixed it with the instructions in this thread. Thank you though. 


[http://ubuntuforums.org/showthread.php?t=965180&highlight=nvidia+gui]("http://ubuntuforums.org/showthread.php?t=965180&highlight=nvidia+gui")

---

