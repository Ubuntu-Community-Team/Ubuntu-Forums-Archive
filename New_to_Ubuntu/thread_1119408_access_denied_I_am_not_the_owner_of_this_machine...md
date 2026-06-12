---
title: "access denied I am not the owner of this machine..."
date: 2009-04-07
forum: New to Ubuntu
---

### Post by Swallace23 on 2009-04-07
Im new to Ubuntu and an having administrative troubles. 

Im trying to install Ampache and I need to safe a config file in my etc/ampache directory but I don't have access to do so. It says root is the only user allowed to change the file permissions. Is there a work around for this?

---

### Post by Iowan on 2009-04-07
Try preceeding your commands with [**sudo**]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Hospadar on 2009-04-07
you should use sudo to do this:
more info here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by RedSingularity on 2009-04-07
Do "sudo nautilus" in the terminal to navigate graphically through files on the system with ROOT privileges.

---

### Post by Swallace23 on 2009-04-07
that worked wonders. Thanks for all the info everyone.

---

