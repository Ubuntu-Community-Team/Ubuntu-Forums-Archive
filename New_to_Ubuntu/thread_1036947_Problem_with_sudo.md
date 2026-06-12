---
title: "Problem with sudo"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by nshailesh on 2009-01-11
I have installed ubuntu 8.04 on windows xp using vmware workstation.
So whenever I log into ubuntu terminal and do sudo ,the terminal does not accept it and throws unable to resolve the host shailesh-desktop(name of my pc) error.
Everytime I have to login as root and do the operations .please help.............

---

### Post by ajcham on 2009-01-11
Could you post the contents of **/etc/hosts** and **/etc/hostname**

---

### Post by blazemore on 2009-01-11
Reboot into Recovery Mode and drop the the root prompt.
Type ```
nano /etc/hosts
```
The line that has shailesh-desktop in it... delete that line (Or put ## in front of it)

---

### Post by zvacet on 2009-01-11
The first two lines in your /etc/hosts file should look like this

127.0.0.1 localhost
127.0.1.1 shailesh-desktop

If they are different then boot in recovery mode and type

```
nano /etc/hosts
```
 and then make changes in lines

---

