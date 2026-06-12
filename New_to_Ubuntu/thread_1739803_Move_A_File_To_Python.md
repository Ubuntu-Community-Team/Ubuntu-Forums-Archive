---
title: "Move A File To Python"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by 6677 on 2011-04-26
I've been trying to move a file to /usr/local/lib/python2.5   but it always blocks be as apparently im not the folder owner. I only got ubuntu on a persistant usb and am very happy with it but i need to be able to move this file to do work. apparently i have to become a root but i have no idea what this means.
Can anyone please help me by telling me how to move a file (its from a memory stick at moment) into the folder above?

---

### Post by TeoBigusGeekus on 2011-04-26
```
sudo mv /path/filename /usr/local/lib/python2.5
```
Replace /path/filename with the actual path and name of your file.
Give your password (it won't be shown), press enter and you're done.

---

### Post by 6677 on 2011-04-26
Thankyou
This worked perfectly. Added it to my pile of notes ive started to help me remember my way around ubuntu

---

### Post by TeoBigusGeekus on 2011-04-26
Check out these two great books:
[http://ubuntu-manual.org/download/10.04e2/en_US/screen]("http://ubuntu-manual.org/download/10.04e2/en_US/screen") - Ubuntu in general
[http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") - the command line

---

