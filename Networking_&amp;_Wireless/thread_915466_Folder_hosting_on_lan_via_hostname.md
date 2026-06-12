---
title: "Folder hosting on lan via hostname"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by wolterh on 2008-09-09
Em... yesterday i found out that if i accessed 

[http://host-name:631/printers](http://host-name:631/printers)

I could see the printers connected to the computer, and started wondering if I could host a folder with files to share with my lan neighbors with some similar address, for example:

[http://host-name:765/portal](http://host-name:765/portal)

with portal being a shared folder...

---

### Post by cariboo on 2008-09-09
Your are only accessing cups, the printing system, it can only be accessed from your computer, if anyone else on the network tries to access it they get a page saying Forbidden. If you want to share files and directories, You will have to set up Samba, for a good howto check here:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Jim

---

### Post by wolterh on 2008-09-10
I'm actually sharing the folder named portal, but I want to be able to access it from firefox and get a list of files and folders inside "portal"

---

### Post by superprash2003 on 2008-09-10
then install apache.. LAMP..

---

