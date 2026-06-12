---
title: "Strange error when installing openSSH"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Nachtkriecher on 2008-03-31
so im trying to install openssh-server with apt-get, and i get this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

we tried setting the JAVA_HOME variable, which for some reason was not set. but that didnt work. anyone know whats going on?

---

### Post by Nachtkriecher on 2008-03-31
nevermind... sorry, found it..

```
sudo apt-get remove sun-java6-doc
```

---

### Post by Eiríkr on 2008-03-31
Glad it's working.  :D  Since this thread is done for you, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

