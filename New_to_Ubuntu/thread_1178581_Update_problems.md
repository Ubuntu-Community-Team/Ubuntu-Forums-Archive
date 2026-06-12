---
title: "Update problems"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Malice007 on 2009-06-04
When I try to update or install anything I get this...

E: psmouse-dkms: subprocess post-installation script returned error exit status 2

How do I get rid of this?

---

### Post by Partyboi2 on 2009-06-05
Hi, can you open a terminal and post the whole output to
```
sudo dpkg --configure -a
```

---

### Post by Malice007 on 2009-06-05
Setting up psmouse-dkms (2.6.20-16.29-1) ...
Loading new psmouse-2.6.20-16.29-1 DKMS files...

Error! Cannot locate /usr/src/psmouse-2.6.20-16.29-1.dkms.tar.gz.
File does not exist.
dpkg: error processing psmouse-dkms (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 psmouse-dkms

Ok I do not want this nor do I want it to install. How do I remove it?

Thanks.

---

### Post by Malice007 on 2009-06-06
Any help other than posting what I got in terminal? please :P

---

### Post by Partyboi2 on 2009-06-06
Open a terminal and remove psmouse-dkms
```
sudo apt-get remove psmouse-dkms
```then
```
sudo dpkg --configure -a
```

---

