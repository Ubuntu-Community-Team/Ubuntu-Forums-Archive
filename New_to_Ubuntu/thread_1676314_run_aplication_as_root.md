---
title: "run aplication as root"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by patchido on 2011-01-27
I am using filezilla as my ftp client, and I have the problem that the files are being stored under var/www so, filezilla has to be executed with sudo privileges in order to write into the folder, but I don't want to be opening a terminal every time I open filezilla, is there anyway to include the command in the launcher?

---

### Post by Vaphell on 2011-01-27
in the command field of the launcher add gksu
```
gksu filezilla
```
for graphical apps one should use gksu not sudo (sudo is for command line tools)

---

### Post by patchido on 2011-01-27
THANKS!

just for learning, what does gksu stand for? just a rndm thing?

---

### Post by Vaphell on 2011-01-27
gksu is like sudo for graphical programs, it informs the system that you expect it to run the program with admin rights. G means that is tailored for gtk/gnome environment, su part can be translated as super-user. KDE desktop uses kdesu.

[http://linux.about.com/cs/linux101/g/gksu.htm](http://linux.about.com/cs/linux101/g/gksu.htm)

---

