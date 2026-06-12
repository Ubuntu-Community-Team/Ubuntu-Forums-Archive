---
title: "sounds folder permissions"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by ajaykumarb on 2011-01-21
I copied a sounds theme Dream to /usr/share/sounds , I was not able to find the option in the sounds settings.
When I tried to change the permissions of Dream folder I accidentally changed the sounds folder permissions using sudo chmod 644 /usr/share/sounds/


.My default theme is also not working .
Can you pls help me to fix this

Thank you
Ajay

---

### Post by ajgreeny on 2011-01-21
You can check the permissions of the /usr/share/sounds folder with ls -l /usr/share and then scroll down to the share folder.  It should show as drwxr-xr-x, ie 755 in octal system, but I'm not sure about everything it contains.

---

### Post by ajaykumarb on 2011-01-22
changed the permissions to 755 .Default theme is working .

Thank you

---

### Post by 3rdalbum on 2011-01-22
In future, don't change the permissions of a system folder just so you can put stuff in it; this is a loosening of security policy and it can also lead to mistakes like the one you made ;-)

Instead, run a file manager as root (type "gksudo nautilus" or install the "nautilus-gksu" right-click menu item from Synaptic) and modify the folder's contents or drop items in as root.

---

