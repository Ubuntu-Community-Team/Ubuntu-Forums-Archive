---
title: "help in installing"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by milan5590 on 2010-09-12
while installing any file these errors are occured in ubunto
mkdir: cannot create directory `/usr/local/lib/pkgconfig: Permission denied
make: [install-libs] Error 1 (ignored)

plz help me to solve these errors

---

### Post by Saint_ on 2010-09-12
Are you using synaptic to install these files? It should be running as root by default, so I'll assume you aren't. You have to put ```
sudo
``` at the very beginning of what you're trying to do so you have permission

---

### Post by wojox on 2010-09-12
> **milan5590 said:**
> while installing any file these errors are occured in ubunto
mkdir: cannot create directory `/usr/local/lib/pkgconfig: Permission denied
make: [install-libs] Error 1 (ignored)

plz help me to solve these errors

You can read up on the importance of using root here [RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

