---
title: "Installing and updating programmes"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by Chough39 on 2010-05-26
When updating or installing a programme I now get the following message following a problem which occurred when trying to install GoogleEarth. 



An error occurred
 The following details are provided
 

 E: ttf-dejavu-extra: subprocess installed post-installation script returned error exit status 1  
 E: ttf-dejavu: dependency problems - leaving unconfigured
 

 

 Clicking on details produces a message similar to that below which is produced if I run sudo dpkg --configure -a in terminal.
 

 

 gerald@gerald-desktop:~$ sudo dpkg --configure -a
 [sudo] password for gerald:  
 Setting up ttf-dejavu-extra (2.29-2) ...
 /etc/defoma/hints/ttf-dejavu-extra.hints: Unable to open, or empty.
 dpkg: error processing ttf-dejavu-extra (--configure):
  subprocess installed post-installation script returned error exit status 1
 dpkg: dependency problems prevent configuration of ttf-dejavu:
  ttf-dejavu depends on ttf-dejavu-extra; however:
   Package ttf-dejavu-extra is not configured yet.
 dpkg: error processing ttf-dejavu (--configure):
  dependency problems - leaving unconfigured
 Errors were encountered while processing:
  ttf-dejavu-extra
  ttf-dejavu
 gerald@gerald-desktop:~$ 



I have tried reinstalling ttf-dejavu ttf-dejavu-core and ttf-dejavu-extra. This has no effect.


What needs to be done please?

---

### Post by philinux on 2010-05-26
[https://bugs.launchpad.net/ubuntu/+source/defoma/+bug/521431](https://bugs.launchpad.net/ubuntu/+source/defoma/+bug/521431)

see post #2

---

### Post by Chough39 on 2010-05-26
Many thanks, problem solved. Chough39

---

