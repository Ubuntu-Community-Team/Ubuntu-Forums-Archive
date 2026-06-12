---
title: "Software installation problem."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by dirtrider1 on 2009-11-19
I'm currently running Ubuntu 9.04  and when I try to install any application it comes up with this error "Only one software management tool is allowed to run at the same time." Also I've checked the system monitor to look for the process but cant find anything and I also tried running the command killall synaptic in the terminal and I tried rebooting but I'm still getting this error. Any help would be great thanks.

---

### Post by gettinoriginal on 2009-11-20
It is not just synaptic, you cannot install if you have any combination of synaptic, terminal, or add/remove open at the same time.

---

### Post by blazemore on 2009-11-20
Rather than hunting around for the errant process, simply log off and on again!
Problem solved.

---

### Post by HarrisonNapper on 2009-11-20
> **gettinoriginal said:**
> It is not just synaptic, you cannot install if you have any combination of synaptic, terminal, or add/remove open at the same time.

Isn't it just any instance of apt? Why would having a terminal open interfere?

---

### Post by gettinoriginal on 2009-11-20
Because the terminal is a software management tool.

---

### Post by mlentink on 2009-11-20
> **gettinoriginal said:**
> Because the terminal is a software management tool.

I don't think that's entirely correct. You can open up a terminal and synaptic just fine. Afaik you just can't run an apt-get command while running synaptic at the same time.

---

### Post by Excedio on 2009-11-20
> **gettinoriginal said:**
> It is not just synaptic, you cannot install if you have any combination of synaptic, terminal, or add/remove open at the same time.
 
Don't forget the Update Manager.

---

### Post by blazemore on 2009-11-20
You can have the terminal open!
You just can't run any apt or dpkg programs from it.
Only one can have access to the "lock" file at a time.

---

### Post by snova on 2009-11-20
> **dirtrider1 said:**
> ... I tried rebooting but I'm still getting this error. Any help would be great thanks.

> **blazemore said:**
> You can have the terminal open!
You just can't run any apt or dpkg programs from it.
Only one can have access to the "lock" file at a time.

If you went as far as to reboot, there can't be any other processes holding the lock. If it's still giving you problems, try removing the lock file manually:

```
sudo rm /var/lib/dpkg/lock
```

---

