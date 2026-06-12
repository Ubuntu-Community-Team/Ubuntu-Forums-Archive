---
title: "some  questions"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by A_M_S on 2009-05-20
Hi!
I'm a new user of ubuntu (just installed ver 9.04). Could anybody help me with some stupid questions please?

Is there any defragmentation software in Ubuntu?

Is there any partition manager in Ubuntu?

It is possible to create restoration points (or something similar)?

what is the most complete sysinfo application available?


tnx!

---

### Post by uupreti on 2009-05-20
I am not sure about defragment tool. But you can use **gparted** for partition manager and you can get system monitor from System menu which will give you very much information about your system.

---

### Post by Mornedhel on 2009-05-20
> **A_M_S said:**
> Is there any defragmentation software in Ubuntu?

You don't need any for ext3 filesystems. 

> **A_M_S said:**
> Is there any partition manager in Ubuntu?

Try GParted. It's in the repositories.

> **A_M_S said:**
>  It is possible to create restoration points (or something similar)?

Never tried.

> **A_M_S said:**
>  what is the most complete sysinfo application available?

Define "sysinfo" ?...

---

### Post by eeeandrew on 2009-05-20
hi, 

I can tell you right away that the ubuntu partition manager is called gparted. Go into terminal and type: 

> sudo apt-get install gparted

to get it.

Basic system information can be found in system->administration->system monitor.

Hope this is useful,
Andrew

---

### Post by Ms_Angel_D on 2009-05-20
Welcome To Ubuntu A_M_S! none of these are stupid questions, and in fact quite a few have been asked before.

> **A_M_S said:**
> Hi!Is there any defragmentation software in Ubuntu?

You don't need to defrag a Linux system (Say goodbye to that windows habit)


> **A_M_S said:**
> Is there any partition manager in Ubuntu?
Gparted go to System -> Administration -> Synaptic Package Manager and search for it.

> **A_M_S said:**
> It is possible to create restoration points (or something similar)?

See this thread [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

> **A_M_S said:**
> what is the most complete sysinfo application available?


Hardinfo go to System -> Administration -> Synaptic Package Manager and search for it.

---

### Post by A_M_S on 2009-05-20
Thank you for your help :D!!!

---

### Post by lovinglinux on 2009-05-20
As far as I know, GParted is installed by default. Just go to "System >> Administration >> Partition Editor".

---

### Post by waspbr on 2009-05-20
nope, it is default in the live CD, but you need to install it for a persistent one.

---

### Post by lovinglinux on 2009-05-20
> **waspbr said:**
> nope, it is default in the live CD, but you need to install it for a persistent one.

I guess I never noticed because I create a list of installed software using *dpkg --get-selections* before re-installing the OS and install them all automatically. So GParted is already there when I need it. ;)

---

### Post by faraz_k86 on 2009-05-20
> I guess I never noticed because I create a list of installed software using dpkg --get-selections before re-installing the OS and install them all automatically. So GParted is already there when I need it.

thats a great command.. I never knew that.. k so once i get the list with that command how do i get a new system to install them automatically??

thx

---

### Post by lovinglinux on 2009-05-20
> **faraz_k86 said:**
> thats a great command.. I never knew that.. k so once i get the list with that command how do i get a new system to install them automatically??

thx

Follow this:

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

### Post by sarum on 2009-05-21
That is so usefull.
Thanks...........sarum.

---

### Post by Bigtime_Scrub on 2009-05-21
> **A_M_S said:**
> Hi!
I'm a new user of ubuntu (just installed ver 9.04). Could anybody help me with some stupid questions please?

Is there any defragmentation software in Ubuntu?

Is there any partition manager in Ubuntu?

It is possible to create restoration points (or something similar)?

what is the most complete sysinfo application available?


tnx!

Most of these questions have been answered by others expect for the restore points. There is nothing really like that in Linux because you kind of/sort of don't need them. You do not get viruses in Linux and when a program creates problems you simply get rid of it. 

There has been some demand for it and while there is still not a real system restore like in Vista there is now a Linux version of system rescue in case something does go wrong. (it is rare but it can happen)

[http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

I hope this link helps you with that.

---

### Post by faraz_k86 on 2009-05-21
> **lovinglinux said:**
> Follow this:

thanks mate :)

---

