---
title: "Removing apps instaled with make"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by A_M_S on 2009-10-06
Hi

One way to remove programs compiled with "make install" is with "make uninstall" right?

Is it necessary to have the aplication source code to run "make uninstall" ?
   
If not, how can i find the directory to run "make uninstall" for a specific application?



tnx.

---

### Post by Kreaper on 2009-10-06
I Think you have to run it in the source code directory, but it will only work if the MAKEFILE has a rule for uninstall

---

### Post by A_M_S on 2009-10-06
Ok.
Thanks for the reply!

---

### Post by MrWES on 2009-10-06
> **A_M_S said:**
> Hi

One way to remove programs compiled with "make install" is with "make uninstall" right?

Is it necessary to have the aplication source code to run "make uninstall" ?
   
If not, how can i find the directory to run "make uninstall" for a specific application?



tnx.

Next time you install an app from the source, you might want to consider using Checkinstall. It'll create an deb package for you and then you can use the Synaptic Package Manager to remove it.
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")


~Bill

---

### Post by A_M_S on 2009-10-06
> **MrWES said:**
> Next time you install an app from the source, you might want to consider using Checkinstall. It'll create an deb package for you and then you can use the Synaptic Package Manager to remove it.
[https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")


~Bill
I will start to use it. :)
Tnx!

---

