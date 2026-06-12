---
title: "authentication and installation"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by Content_dog on 2010-12-19
when i try to install something the package installer it says i must close all other software managment programs, even when nothing is open.

Ive tried even restarting! i still get this message. any help?

Thanks!
Content_dog

([SIZE="5"]P.S, one tiny detail. Im...[/SIZE][SIZE="4"]kinda...[/SIZE][SIZE="3"]sorta...[/SIZE][SIZE="2"]err uhh...running...[/SIZE][SIZE="1"]linux mint...[/SIZE]

---

### Post by JC Cheloven on 2010-12-19
> **Content_dog said:**
> ([SIZE="5"]P.S, one tiny detail. Im...[/SIZE][SIZE="4"]kinda...[/SIZE][SIZE="3"]sorta...[/SIZE][SIZE="2"]err uhh...running...[/SIZE][SIZE="1"]linux mint...[/SIZE]
LOL

Regarding your problem: the system is reporting that another instance of the package manager (in the form of apt-get, aptitude, synaptic, or whatever) is already running when you try to install something. This may be due to some misconfiguration caused by a missing update or the like. First try in a terminal
```
sudo dpkg-reconfigure -a
``` (may take a while)

Or you can have a look in the system monitor (using gnome-mint, right?) to see if some form of the package manager is running, and eventually try to kill it from there.

Hope this helps

---

### Post by Content_dog on 2010-12-20
> **JC Cheloven said:**
> First try in a terminal
```
sudo dpkg-reconfigure -a
``` (may take a while)

Hope this helps

Worked perfectly. Thanks a lot!

---

### Post by JC Cheloven on 2010-12-21
Glad it worked. 
Please take a moment to mark the thread as solved (in Thread Tools, at the top of the page), so that others can also benefit.

---

