---
title: "NIS system UID/GID definition"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by KenLiou on 2007-04-19
ubuntu system/service UID/GIDs are based on the order of the service/software been installed, so there is no fixed system UID/GID on every system which is running ubuntu, this practice stop us from using ubuntu on our NIS environment.  

Almost all the Unix system defined a fixed system/service UID/GID under 100, but ubuntu start from 100 and up without definition and they are overlapped with current UID/GID table on NIS server, since we dist out the local passwd and group files to all the systems on the network to maintain the credential integrity of all the systems, it is not possible to use ubuntu. 

Suggestion....

Ken

---

