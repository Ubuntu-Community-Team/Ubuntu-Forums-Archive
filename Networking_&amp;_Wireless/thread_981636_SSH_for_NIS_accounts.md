---
title: "SSH for NIS accounts"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by wimmelis on 2008-11-13
Dear all, 


Is there any special configuration required to allow NIS accounts to ssh to an NIS client ?
I have NIS working locally, and ssh works for local accounts, but not for the NIS ones, as then I get "Permission denied, try again."
I read one of the requirements is for the sshd_config file to have UsePAM yes, which it does.
Anything more ? Anyone ?


Thanks,

WM

---

### Post by wimmelis on 2008-11-17
Dear all, 


After digging into the log files of the server and debugging modes on the client, it appeared that the NIS server expected the tcsh shell, which was installed, but not at the expected location. Creating a symbolic link to the real location solved the problem :).



WM

---

