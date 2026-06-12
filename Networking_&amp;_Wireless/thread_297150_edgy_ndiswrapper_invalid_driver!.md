---
title: "edgy ndiswrapper invalid driver!"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by bags on 2006-11-10
hy everybody!
I don't speak english very well but I'll try to explain my problem.. I uninstalled all the ndiswrapper versions and ndiswrapper-common from my system and I installed ndiswrapper-1.28 from the tarball of the official site as someone suggested to.

this is what happens when I try to get my wireless working (It worked fine under Dapper!)

> matteo@matteo-laptop:~/Desktop/3CRWE154G72_Jul_08_04/3CRWE154G72_Jul_08_04/DISK1/Driver$ sudo ndiswrapper -i 3C154G72.INF 
installing 3c154g72 ...
forcing parameter EnableRadio from 0 to 1
forcing parameter EnableRadio from 0 to 1
matteo@matteo-laptop:~/Desktop/3CRWE154G72_Jul_08_04/3CRWE154G72_Jul_08_04/DISK1/Driver$ sudo ndiswrapper -l
installed drivers:
3c154g72        invalid driver!
matteo@matteo-laptop:~/Desktop/3CRWE154G72_Jul_08_04/3CRWE154G72_Jul_08_04/DISK1/Driver$

I really don't know why I get an invalid driver error; the driver it's the same that I used under Dapper!

Any help would be very appreciated and rewarded with pasta :-D

---

### Post by gitargr8 on 2006-11-10
Are there any other .inf files that come with your driver? Navigate to the driver directory and run

```
ls | grep *.inf
```

Try installing the other .inf files with ndiswrapper.

```
sudo ndiswrapper -i otherfiles.inf
```

Then run

```
ndiswrapper -l
```

to see if any others worked.

---

### Post by bags on 2006-11-10
unfortunately there are not more *inf files ](*,) 

> 
matteo@matteo-laptop:~/Desktop/3CRWE154G72_Jul_08_04/3CRWE154G72_Jul_08_04/DISK1/Driver$ ll
total 1076
-rwxr--r-- 1 matteo matteo 386432 2006-11-10 22:37 3C154G7251.sys
-rwxr--r-- 1 matteo matteo      0 2006-11-10 22:37 3C154G72.CAT
-rwxr--r-- 1 matteo matteo  13382 2006-11-10 22:37 3C154G72.INF
-rwxr--r-- 1 matteo matteo 387850 2006-11-10 22:37 3C154G72.sys
-rwxr--r-- 1 matteo matteo  16831 2006-11-10 22:37 CCU3C154.dll
-rwxr--r-- 1 matteo matteo 225280 2006-11-10 22:37 CCU3C154.EXE
-rwxr--r-- 1 matteo matteo  13382 2006-11-10 22:37 Driver.2K
-rwxr--r-- 1 matteo matteo  13388 2006-11-10 22:37 Driver.98
-rwxr--r-- 1 matteo matteo  13388 2006-11-10 22:37 Driver.ME

---

