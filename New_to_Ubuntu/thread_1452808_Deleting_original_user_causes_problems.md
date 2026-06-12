---
title: "Deleting original user causes problems?"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by japhyr on 2010-04-12
Hello,

I am running a project in which a number of students install ubuntu onto older computers.  Some students have left the project, and when they left we added a new user with admin privileges, and deleted the original user.  We notice the computer still retains the name the student who did the installation gave the computer.

Will this cause any definite problems?  Some computers are having trouble with things like installing printers, and I am wondering if this might be the cause.

---

### Post by readycarpenter on 2010-04-12
the name of the pc, is not the associated with any user. you can rename the pc in Ubuntu via
System > Administration > Networking > General tab > Host name field

ubuntu by default names a pc, user-desktop or user-laptop

cheers

---

### Post by philinux on 2010-04-12
> **readycarpenter said:**
> the name of the pc, is not the associated with any user. you can rename the pc in Ubuntu via
System > Administration > Networking > General tab > Host name field

ubuntu by default names a pc, user-desktop or user-laptop

cheers

+1.

For anyone else reading this thread, later releases than jaunty need this.
```
gksudo gedit /etc/hosts 

and

gksudo gedit /etc/hostname
```

---

