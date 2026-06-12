---
title: "how to install jboss and java?"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by jonneymendoza on 2011-03-15
Hi. i am currently running ubuntu server edition, the latest version and  was wondering how do i install jboss and java if possible?

thanks in advance

---

### Post by jonneymendoza on 2011-03-15
edit: i have tried this command: sudo apt-get install sun-java6-jdk 


and this is what happens.

Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate

---

### Post by oldos2er on 2011-03-15
Open your sources.list ```
sudo nano /etc/apt/sources.list
``` Remove the comment marks from the partner repository lines:

deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner
deb-src [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick partner

Save and exit, run ```
sudo apt-get update && sudo apt-get install sun-java6-jdk
```

---

### Post by jonneymendoza on 2011-03-15
thanks. installing java now. next question. is there a jboss package around? Is there a command to see what packages i can install? like a full list?

---

### Post by oldos2er on 2011-03-15
**apt-cache search jboss** will show all possible 'jboss' packages. For details on one specific package, use **apt-cache show jbossas4** for example.

**aptitude** is a complete CLI package manager. It is not installed by default anymore in 10.10 desktop version, not sure about server version. **sudo apt-get install aptitude** will grab it.

[http://wiki.debian.org/Aptitude](http://wiki.debian.org/Aptitude)

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)

**dpkg** is yet another program to manipulate packages, **man dpkg**

---

