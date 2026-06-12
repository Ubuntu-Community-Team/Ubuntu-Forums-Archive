---
title: "How to install '...Linux-x86-Install' file via Command Line"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by u bun tu on 2011-08-22
Hello Everyone,

I have downloaded a file '*-Linux-x86-Install' file from the following website:

[https://gforge.ti.com/gf/project/wilink_drivers/frs/](https://gforge.ti.com/gf/project/wilink_drivers/frs/)

How do I install the file via command line?

I know I can go through the GUI and double click on the file but I am remotely logging (SSH) in and I only have access through the command line.

If anyone can help, I would appreciate it.

Thanks!

---

### Post by 123456789123456789123456 on 2011-08-23
try sudo ./*-Linux-x86-Install

if it is a .install file, or .sh file that should work.
if not ./ and the file name should work without sudo access.
if it is a deb file, then sudo dpkg -i and the pacage name will install it.
hope this helps.

---

### Post by sidzen on 2011-08-23
> **u bun tu said:**
> Hello Everyone,

I have downloaded a file '*-Linux-x86-Install' file from the following website:

[https://gforge.ti.com/gf/project/wilink_drivers/frs/](https://gforge.ti.com/gf/project/wilink_drivers/frs/)

How do I install the file via command line?

I know I can go through the GUI and double click on the file but I am remotely logging (SSH) in and I only have access through the command line.

If anyone can help, I would appreciate it.

Thanks!
 Perhaps --
place file where desired in the system
[PHP]chmod +x path/to/Installfile[/PHP]cd to folder where Install file resides
[PHP]./Installfile[/PHP]

---

