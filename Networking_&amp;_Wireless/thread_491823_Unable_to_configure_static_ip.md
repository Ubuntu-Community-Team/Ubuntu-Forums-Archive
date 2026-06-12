---
title: "Unable to configure static ip"
date: 2007-07-04
forum: Networking &amp; Wireless
---

### Post by dwilliams07 on 2007-07-04
Hello,

I'm new to LInux and having a hard time performing what I'm sure is a simple task.  I installed 6.06.1 server without any problems.  For some reason, I don't know how to exit out of the vi /etc/network/interfaces screen after  entering the static ip I want.  I just want to save the new settings and restart the interface.  I've checked a few places on the net and after entering the default gateway they all just read "restart interface.  Please help.  Thanks

---

### Post by Analord on 2007-07-04
Vi editor is not for beginners.

i reccomend using nano or gedit. 
From nano you just save with ctrl o and exit with ctrl x.

U can restart your network interface by issuing a command from terminal
sudo /etc/init.d/networking restart

---

### Post by dwilliams07 on 2007-07-05
Thanks.  So I can just download nano or gedit from a repository?  I'll try it tonight and let you know if I was successful.  Thanks again.

---

### Post by mpeters on 2007-07-05
> **dwilliams07 said:**
> Hello,

I'm new to LInux and having a hard time performing what I'm sure is a simple task.  I installed 6.06.1 server without any problems.  For some reason, I don't know how to exit out of the vi /etc/network/interfaces screen after  entering the static ip I want.  I just want to save the new settings and restart the interface.  I've checked a few places on the net and after entering the default gateway they all just read "restart interface.  Please help.  Thanks

To save and exit from vi, hit Esc and type :wq (that's a colon followed by "w" for write and a "q" for quit)

---

### Post by dwilliams07 on 2007-07-07
Thanks analord and mpeters.  I have my static ip configured!

---

### Post by kevdog on 2007-07-07
Sorry a little bit late but with vi, to exit and save hit cntrl-zz (that's z twice). Kind of a shortcut!

---

