---
title: "JMP statistical software and Trimble Pathfinder Office"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by jipock on 2009-09-23
IM considering over to this OS however I am afraid that doing so will interfere with some other software that are currently run often in both school and work.  Does Ubuntu have the capability on its own or through upgrades to run JMP statistical software, Trimble's Pathfinder Office and TerraSync GeoExplorer?

---

### Post by fraser_m on 2009-09-23
If it's Windows software, check out winehq.org to see if it'll work. If not, you can probably use VirtualBox or another virtualization solution.

---

### Post by ikt on 2009-09-23
if all else fails chuck ubuntu on a spare machine, install wine and see if they run, some quick googling suggests it's unlikely they're compatible :(

If you get a chance send an email to the official support channels of that software and see if they plan on releasing a linux version or know of linux compatible software. :)

best of luck


> **fraser_m said:**
> If it's Windows software, check out winehq.org to see if it'll work. If not, you can probably use VirtualBox or another virtualization solution.


Virtualbox looks like the main solution.

---

### Post by fraser_m on 2009-09-23
According to the JMP website, they have a native Linux client of their software.

---

### Post by Jordy_224 on 2010-11-06
Hello, 
I use JMP statistical software and need help trouble shooting the  installation using WINE. There is a odd graphics issue. The graphics for certain windows are misaligned. Attached to the post are are screen shots

Details: 
At load there is a ODBC Error:

```
ODBC Error: Unable to allocate Environmental handle

```

Please note that I have installed JMP using wine with a previous version ( 1yr ago) of wine / jmp / and Xubuntu distribution  software u
I do not have a license for the Linux version. 

It is a graphical issue but I am  not sure where to proceed next. 

```
xbuntu 10.04 
Wine 1.2
JMP 8.02
Graphics: Linux-x86; driver: 96.43.18
 
```

---

### Post by Jordy_224 on 2011-02-20
Update: 

 After updating the ati driver using xorg-edgers and updating the wine direct x version I program prompts the same error.

---

### Post by Jordy_224 on 2011-02-27
bump

---

