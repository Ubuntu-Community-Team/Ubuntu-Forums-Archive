---
title: "Password not accepted, to  login  from network winxp pc, into my ubuntu"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by antonet on 2007-12-19
Hi
I can not login into my ubuntu from another  winxp computer to access ubuntu shared folders.
I can see the ubuntu  pc from winxp  into my workgroup network.
The ubuntu  pc  named "antonis" ,the admin user is "antonis" and pasword is like 123456.(User antonis is member of antonis group,and is the administrator)
But when compete username/password  from winxp pc, i can not login.
(I tried to change group for username  "antonis"  from "antonis" group to "root","admin" but nothing)
The strange is that, from ubuntu pc, i can login into my winxp pc.
Any idea?

---

### Post by wharp on 2007-12-19
Have you installed and configured Samba and setup the shares?

---

### Post by AlanRogers on 2007-12-19
Please search the forum for configuring shared folders or Samba. This has been covered any number of times before, such as here - [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by antonet on 2007-12-19
OK. thanx

Just find the solution.
The problem was about  the sambausers files
I put the code 
system_username = "antonis"
Its OK now! thanx  :)

---

