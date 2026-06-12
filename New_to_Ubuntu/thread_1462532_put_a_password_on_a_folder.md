---
title: "put a password on a folder"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by computerguts on 2010-04-25
How would you put a password on a folder in ubuntu?

either when you try to open the folder it prompts you for a password or apply a password on all the contents of a folder so that when you try to open any file in that folder you are prompted for a password. 

Thanks

---

### Post by ibuclaw on 2010-04-25
You may want to look at various encryption options available. Some people swear by truecrypt, however normal gnupg should do just fine. Installing seahorse-plugins will add encryption options into the right-click menu for Gnome.

Regards

---

### Post by tica vun on 2010-04-25
Note however that actually encrypting the data will render it basically unrecoverable if you so much as lose the password. If the issue is keeping it from other users, making sure you put it in folders they don't have read access to (ie, your home folder) should do it.

---

