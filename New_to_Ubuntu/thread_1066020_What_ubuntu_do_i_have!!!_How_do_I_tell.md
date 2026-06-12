---
title: "What ubuntu do i have!!?! How do I tell?"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by listerdl on 2009-02-10
Hi I know that I installed Hardy Heron - but I think that I also upgraded to Ibex - how do I tell?

THANKS!!

---

### Post by dca on 2009-02-10
Easiest (quickest) way w/o CLI is try going to 'System -> About Ubuntu' from menu bar...  Don't know if that part gets updated though when moving from vers to vers...

---

### Post by philinux on 2009-02-10
In a terminal

```
uname -a
```

Or system>admin>system monitor - system tab

---

### Post by bluelamp999 on 2009-02-10
Hi,

From the System menu, go Administration>System Monitor and select the System tab...

---

### Post by niteshifter on 2009-02-10
Hi,

In a terminal enter:
```
cat /etc/lsb-release
```

That will produce output like this:
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

---

### Post by egalvan on 2009-02-10
"System>Administration>System Monitor and select the System tab..."

This gave me
"Release 8.04 (hardy)
Kernel Linux 2.6.24-23 generic"

along with other usefule info...

System menu, go Administration>System Monitor and select the System tab...


typing

```
cat /etc/lsb-release
```

gave me this further useful info...

```
ernest@gx280:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.2"
ernest@gx280:~$ 
```


Depends on what info one needs or wants...

---

### Post by LowSky on 2009-02-10
open firefox and go to help and click on about firefox. at the botom it will tell you what version firefox and your OS

---

### Post by UbuntuNerd on 2009-02-10
go to application > accessories > terminal and type this code:
```
lsb_release -a
```

---

