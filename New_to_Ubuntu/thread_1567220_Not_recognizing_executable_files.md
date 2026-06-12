---
title: "Not recognizing executable files"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-09-03
Ok, so I am an absolute Linux newbie.  Total noooob.  I installed the latest Ubuntu yesterday and am now trying to set it up similar to my old Windows installation.  Priority 1 was installing Java & NetBeans.  I downloaded the latest NetBeans with full Java but cannot seem to start the installation.  It comes as a .sh file.  In browsing this forum I found a thread that told me I needed to change the permission of the file to run as a program, which I did.  I then clicked "run" and  nothing happened.  I opened it again and this time selected "run in terminal".  The terminal opened and then promptly closed, accomplishing nothing.  From a completely new and slightly intimidated by the whole terminal thing standpoint, what am I doing wrong here?

---

### Post by oldos2er on 2010-09-03
Go to menus System, Administration, Software Sources, Other Software tab, enable the partner repository. Use Ubuntu Software Center, Synaptic Package Manager, or apt-get to install java and netbeans. ```
sudo apt-get update && sudo apt-get install netbeans sun-java6-jre sun-java6-jdk
```

---

### Post by ubunwhat on 2010-09-03
You, Madam, are a rock star.

---

### Post by oldos2er on 2010-09-03
You're welcome.   :)

---

