---
title: "apt-get interrupted"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by mevets on 2009-03-19
I was using apt-get to install something and I was rushing and closed the terminal before it was done installing. This royally screws up dpkg so I ran dpkg --configure -a and it finished the install process. The problem now is that none of my apps can run as root. They all say it failed. I figure this is a common problem. Does anyone know how to fix this?

---

### Post by nelskurian on 2009-03-19
bump..

---

### Post by sahabcse on 2009-03-19
Hi

Paste the error log  tail -f /var/log/apt/term.log

---

### Post by nelskurian on 2009-03-19
Your authentication worked fine.It sures that you have in admin group.But some other factor kill the the process..To check that you have to analyse the log's.
Can you able to do sudo or gksu from terminal.I think in gui-authentication You have the mentined problem.

---

