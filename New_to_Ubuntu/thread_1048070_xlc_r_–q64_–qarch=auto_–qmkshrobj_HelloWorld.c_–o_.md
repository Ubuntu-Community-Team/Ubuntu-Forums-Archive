---
title: "xlc_r –q64 –qarch=auto –qmkshrobj HelloWorld.c –o libhello.so"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by void_void on 2009-01-23
i am going through 

[http://www.ibm.com/developerworks/systems/library/es-jniexamples.html](http://www.ibm.com/developerworks/systems/library/es-jniexamples.html)
 
but when i am trying following command it gives the error

xlc_r –q64 –qarch=auto –qmkshrobj HelloWorld.c –o libhello.so

bash: xlc_r: command not found

from where i can download this package

---

### Post by moonoo on 2009-01-23
Obvious one here, but have you tried the repositories?

Sudo apt-get install xlc_r

Not sure if its there... Maybe it comes as a .deb from the web page your playing with?

Whats is it suppose to do? Looks to me like a compiler command.

---

### Post by void_void on 2009-01-23
ya it is compile command it produces ".so" file

---

### Post by void_void on 2009-01-23
sudo apt-get install xlc_r 
is not working....

---

### Post by moonoo on 2009-01-23
looking at the website its an IBM c/c++ compiler so I would start there for the *.tar.gz/*.deb file.

---

### Post by mckenzm on 2012-09-04
If anyone else is reading this, a solution would be to try with g++ or gcc instead.

The xlC binaries for AIX will be big-endian and possibly powerPC running AIX optimised.  

Coming from little-endian AIX you would use gcc.  

Suspect OP was porting something to Ubuntu,  The build processes invariably need tweaking, and cannot just be copied over and run.

---

