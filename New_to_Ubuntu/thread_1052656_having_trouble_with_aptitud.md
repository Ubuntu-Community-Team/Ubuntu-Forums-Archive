---
title: "having trouble with aptitud"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Vicfred on 2009-01-28
I have 2 broken packages, tried to fix them by selecting the broken packages in aptitud... well actually everytime I install something it fails and fix the previously broken package, first vlc broke, then evolution and evolution-common, now bzr. What's happening?

---

### Post by fugaki on 2009-01-28
try this in synaptic:
Edit>Fix Broken Packages

---

### Post by Vicfred on 2009-01-28
that's not working

E: /var/cache/apt/archives/bzr_1.6.1-1_i386.deb: failed in buffer_write(fd) (10, ret=-1)

---

### Post by Vicfred on 2009-01-28
bump

---

### Post by Vicfred on 2009-01-28
bump

---

### Post by kshtjsnghl on 2009-01-29
you should try the command -
 
sudo dpkg --configure -a

---

### Post by kshtjsnghl on 2009-01-29
you may also want to remove the packages that are broken if the above command doesnt work by using 

sudo apt-get --purge remove <package name>

---

