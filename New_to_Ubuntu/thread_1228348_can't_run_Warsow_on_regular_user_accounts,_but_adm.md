---
title: "can't run Warsow on regular user accounts, but admin accounts work fine."
date: 2009-07-31
forum: New to Ubuntu
---

### Post by canthus13 on 2009-07-31
When attempting to run Warsow on a regular user account, I get "your openGL installation doesn't support direct rendering" And something about needing to install proprietary drivers.  The proprietary nvidia drivers are installed and work fine, as Warsow runs perfectly on admin accounts.  What sort of permissions would interfere with opengl?

--Me

---

### Post by Kai Summers on 2009-07-31
Adjust the Warsow Launcher command to always run as root. Something like

gksu "exsisting command"
or
gksudo "exsisting command" 

For the first instance "gksu" the ROOT password will be needed for the Second instance "gksudo" the user password will be required.

If you don't want to be asked your password everytime edit your visudo
export EDITOR=gedit && sudo visudo

---

