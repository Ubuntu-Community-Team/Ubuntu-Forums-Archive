---
title: "Access Permision Restricted File"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by iWill on 2007-04-17
Ok so im trying to install the driver with ndiswrapper for the netgear WPN111. So ive downloaded the exe file on the website and extracted it with cabextract. Then opened with unshield but now i need to access the file with .sys and .inf file but i cant since permissions wont let me....is there a way to open this file?

---

### Post by HumanAnarchist on 2007-04-17
use "sudo nano NAMEOFFILE.sys" to edit in the terminal 

or

"gksudo gedit NAMEOFFILE.sys"

-ha-

---

### Post by iWill on 2007-04-17
Thanks...but i need those .sys and .inf files to use with ndiswrapper and therefore need to copy them in the same directory...which i suppose isnt possible since i dont have permission...right?

---

### Post by crosintoski on 2007-04-17
Try this chown tutorial

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_ownership](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_change_files.2Ffolders_ownership)

---

### Post by HumanAnarchist on 2007-04-17
that's true, but you can get access to the files by using some commands in the terminal with the help of sudo

in the directory/folder where your files are type this: 

```
sudo chmod 777 * 
``` 

The command changes the permision of all the files so all users on your system can both, read, write and delte the files. 

-ha-

---

### Post by iWill on 2007-04-17
Great Thanks it worked!

---

