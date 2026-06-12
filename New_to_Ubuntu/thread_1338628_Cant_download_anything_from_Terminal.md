---
title: "Cant download anything from Terminal"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by momrocker on 2009-11-26
I was doing my usual search for a good theme on the terminal (apt-cache search theme), and i tried to download one and it wouldn't work and I got the following error:

ethanmasse@ethanmasse-desktop:~$ sudo apt-get install emerald
[sudo] password for ethanmasse: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ethanmasse@ethanmasse-desktop:~$ 

^^This was later when i was trying to download Emerald but its the same error. I know what to enter into the terminal, and i did the code right, i know that, so i don't need too much babying in that sense, I just need help with the error itself.

---

### Post by desperado665 on 2009-11-26
Make sure synaptic and update manager are closed.

---

### Post by mbzn on 2009-11-26
Seems like you have another process using the package manager.

---

### Post by lisati on 2009-11-26
> **momrocker said:**
> 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), [COLOR="Red"]is another process using it?[/COLOR]


As others have said, check that something else isn't trying to update your system, e.g. sypantic, update manager, Add/Remove (a.k.a. software cener in 9.10)

---

### Post by momrocker on 2009-11-26
I rebooted my computer and it worked. I guess it may have been running in the background?? Because all i had open was the terminal and songbird, and i dont know why songbird would be giving me that error. Oh well, problem solved.:D

---

### Post by lisati on 2009-11-26
> **momrocker said:**
> I rebooted my computer and it worked. I guess it may have been [COLOR="Red"]running in the background[/COLOR]?? Because all i had open was the terminal and songbird, and i dont know why songbird would be giving me that error. Oh well, problem solved.:D

It's possible. Update manager sometimes runs in the background to automatically check for updates. I've occasionally noticed a little extra disk activity shortly before update manager automatically pops up a window to let me know there are new updates.

---

