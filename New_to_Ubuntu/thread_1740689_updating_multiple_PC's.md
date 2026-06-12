---
title: "updating multiple PC's"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by georgelappies on 2011-04-27
Hi all, I have the following scenario. Only one machine is connected to the internet (and only this machine will ever be connected, no internet connection sharing will be used). A few other machines with the same hardware is located in the room as well and is networked to each other but not to the machine connected to internet (think class room).

If I install ubuntu on all the machines and only do an online update every other day on the one machine connected to the internet. Will it work if I copy the /var/cache/apt folder to each of the other machines? How will these machines know what updates are available to them?

Basically I do not want to update 20 exactly the same installations separately every time as the bandwith is not uncapped. 

Any help will be greatly appreciated. 

Thanks 

George

---

### Post by nothingspecial on 2011-04-27
Search the archive by modification time, copy to a stick and then install all the debs on each computer.

That being said, over the period of the six month Ubuntu release cycle, you only tend to get security updates and bug fixes.

If everything works, you don't need the bug fixes and since these computers are not connected to the outside world you don't need the security updates.

If it were me, I'd make sure the applications you want to use work correctly then leave them as they are.

---

### Post by madjr on 2011-04-27
install aptoncd

---

### Post by georgelappies on 2011-04-27
> **nothingspecial said:**
> Search the archive by modification time, copy to a stick and then install all the debs on each computer.

That being said, over the period of the six month Ubuntu release cycle, you only tend to get security updates and bug fixes.

If everything works, you don't need the bug fixes and since these computers are not connected to the outside world you don't need the security updates.

If it were me, I'd make sure the applications you want to use work correctly then leave them as they are.

Interesting proposal you gave me. In general is no new functionality added to existing programs in the 6 months after release? Only bug fixes and security issues for existing packages?

---

### Post by georgelappies on 2011-04-27
> **madjr said:**
> install aptoncd

Thanks, this is brilliant and will suffice.

---

### Post by madjr on 2011-04-27
> **georgelappies said:**
> Interesting proposal you gave me. In general is no new functionality added to existing programs in the 6 months after release? Only bug fixes and security issues for existing packages?

no, sometimes you will also get updated versions of programs you have installed (like firefox, chromium, libreoffice, etc.)

or if you added a PPA repository (software source) for a program, updates will also come through there.

---

### Post by adit on 2011-04-27
Use Keryx
_[http://keryxproject.org/](http://keryxproject.org/)_

---

