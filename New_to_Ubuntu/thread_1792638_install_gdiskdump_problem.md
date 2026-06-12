---
title: "install gdiskdump problem"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-06-28
I am trying to install gdiskdump as shown here
[http://www.ubuntugeek.com/gdiskdump-gui-for-diskdump-dd.html#more-12122]("http://www.ubuntugeek.com/gdiskdump-gui-for-diskdump-dd.html#more-12122")
when I try to install in software center I get this error
Dependency not satisfiable: (python>_2.7). But I have python 2.6,2.7,and 3.1 installed
When I try it in terminal I get this
```

cmcanulty@HP:~/Desktop$ sudo dpkg -i gdiskdump_0.7.1_all.deb
Selecting previously deselected package gdiskdump.
(Reading database ... 246414 files and directories currently installed.)
Unpacking gdiskdump (from gdiskdump_0.7.1_all.deb) ...
dpkg: dependency problems prevent configuration of gdiskdump:
 gdiskdump depends on python (>= 2.7); however:
  Version of python on system is 2.6.6-2ubuntu2.
dpkg: error processing gdiskdump (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 gdiskdump
cmcanulty@HP:~/Desktop$
```
However I have python 2.7 installed see screenshot

---

### Post by climhazzard36 on 2011-06-28
You could try un-installing any python version lower than 2.7 and see if it works then?

---

### Post by andy8m1 on 2011-06-29
Try to install gdiskdump 0.5 > [https://launchpad.net/gdiskdump]("https://launchpad.net/gdiskdump")

---

### Post by cmcanulty on 2011-06-29
That is the one I am trying to install as shown ion the screenshots above. Thank you

---

### Post by psusi on 2011-06-29
I suggest that you use ghost4linux or partclone or another utility that actually understands what it is copying instead of one that blindly copies everything, including the free space.

---

### Post by dcsoldschool53 on 2011-06-29
Even though you have python 2.7 installed, it is trying to use 2.6 to install the program. It says```
gdiskdump depends on python (>= 2.7); however:   Version of python on system is 2.6.6-2ubuntu2.
```It is not recognizing phython 2.7. Maybe in the Synaptic Manager remove python 2.6 and try it again.

---

### Post by dcsoldschool53 on 2011-06-29
> **cmcanulty said:**
> That is the one I am trying to install as shown ion the screenshots above. Thank you

Actually, as I was viewing your screenshots and your post, everything I saw, showed that you are trying to install gdiskdump_0.7.1 on Maverick. Gdiskdump 0.7.1 is for natty.```
cmcanulty@HP:~/Desktop$ sudo dpkg -i gdiskdump_0.7.1_all.deb
``` Try using gdiskdump 0.5 for maverick that is the OS that  you are using right.

---

### Post by cmcanulty on 2011-06-29
Oh great that was the problem got it now. Thanks!

---

