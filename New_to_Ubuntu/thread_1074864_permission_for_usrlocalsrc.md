---
title: "permission for /usr/local/src"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-02-19
Need to change permissions for /usr/local/src to put the NASM compiler
there. I got this instruction from the NASM site. But to become a superuser for a short time I need a password and don't know what that is.
I type su then it asks for a pW.
Want to change the permissions to "666" using chmod. 
Thanks for any help.

---

### Post by taurus on 2009-02-19
If you want to copy something to /usr/local/src. append a sudo in front of the command to give you root privilege.  Use the same password that you log in with, assuming you have root privilege (the original user that you created during the installing process).

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

