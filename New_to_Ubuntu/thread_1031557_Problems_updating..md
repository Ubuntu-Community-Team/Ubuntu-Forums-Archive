---
title: "Problems updating."
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Dareth on 2009-01-05
This is the window that pops up whenever I try to install updates.

I've tried entering "dpkg --configure -a" in the terminal, but it says I need super user privileges.

---

### Post by avtolle on 2009-01-05
You need to input ```
sudo dpkg --configure -a
```in the terminal, then when prompted enter your password (it will not be reflected) and press enter.

---

### Post by Dareth on 2009-01-06
Thank you. What exactly did I just do? Why did I have to enter it manually?

---

### Post by JoshuaRL on 2009-01-06
It used dpkg to fix the broken dependencies.  It needs root priviledges to run, so that's why you had to run it yourself in the terminal.  If you had gone to Synaptic and asked it fix broken packages, that would be among the things it would do.

Also it would be a good idea to run:
```

sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

```
The first tries to do the same as the dpkg command, but with APT.  The second and third update the system, and the last removes old packages that are no longer needed and are cluttering up the system.

If you want to learn more about the terminal and what the commands mean, check out the link in my sig "Learn the Terminal".  Really great resource.  Hope that helps!

---

### Post by rinka on 2009-01-14
thanks

---

