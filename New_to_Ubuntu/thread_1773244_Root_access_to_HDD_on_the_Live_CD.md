---
title: "Root access to HDD on the Live CD?"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by Brushstroke on 2011-06-01
Hi. How do I get root access to my hard drive while I'm on the live CD? Specifically, I want to edit /etc/sysctl.conf on the HDD right now before I reboot and set the swappiness to 10. It's a new install.

Thanks!

---

### Post by wolfen69 on 2011-06-01
```
sudo su
```

---

### Post by sisco311 on 2011-06-01
It's
```
sudo -i
```
if you want a root shell, or
```
gksu nautilus
```
if you want to start the file manager as root.

---

