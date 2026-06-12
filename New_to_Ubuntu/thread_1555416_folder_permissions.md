---
title: "folder permissions"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Someone uk on 2010-08-18
when i first installed ubuntu i move my old windows "My documents" folder to /home and found that all the folders have been set to root access only
i know how to manually change the permissions of each folder in nautilus however it would take ages for me to change the permissions of every folder so i want to ask if there is a way in terminal to change the permissions of all the folder and all the folders within the folders in one go?

---

### Post by Gone fishing on 2010-08-18
You will need the chown command open a terminal and then

sudo chown -R yourusername /home/yourusername/mydocs

obviously change the above to your situation

have a look at

[http://publib.boulder.ibm.com/infocenter/aix/v6r1/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds1/chown.htm](http://publib.boulder.ibm.com/infocenter/aix/v6r1/index.jsp?topic=/com.ibm.aix.cmds/doc/aixcmds1/chown.htm)

---

### Post by fatality_uk on 2010-08-18
[http://linuxmanpages.com/man1/chown.1.php](http://linuxmanpages.com/man1/chown.1.php)

---

