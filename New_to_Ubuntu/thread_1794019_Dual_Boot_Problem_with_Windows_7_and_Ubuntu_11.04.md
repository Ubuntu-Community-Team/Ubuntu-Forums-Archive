---
title: "Dual Boot Problem with Windows 7 and Ubuntu 11.04"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by n9zf on 2011-06-30
Hi All,
This has been a nagging issue and I have't been able to fix it. If you can help, I'd appreciate it!
 
I have  Compaq CQ50 laptop with Windoze 7 installed. I installed Ubuntu 11.04 and creted a dual boot system. This worked great up until some Windoze update and thereafter, if I run Ubuntu, the next boot into Windoze fails and I have to go through  many minutes of inserting the W7 CD and going throuhg a restore/repair process.
 
On bootup, I do get the choice of a couple of variations of Ubuntu, Windows 7 and the original Vista (which is hidden on a small partition along with the Compaq recovery stuff).
 
I tried using a suggested partition tool (EBCD?) but it would not find the Ubuntu Partition... so not much use.
 
I am slowly reaching a point whre I have to also ask how to uninstall 11.04 and get rid of GRUB and try this on a clean non-dual boot machine.
 
Suggestions?

---

### Post by Mr Stoozer on 2011-06-30
Have both Windows and Ubuntu installation media handy.
Boot into the Windows install DVD and repair the Windows boot loader (an update would not have modified this at all).
Something like this should do it;
```
bootrec /fixboot
```
```
bootrec /fixmbr
```

Then, [reinstall GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB2") to the MBR, not the partition Ubuntu is installed on (ie. sda not sda4).

---

### Post by ajgreeny on 2011-06-30
> **Mr Stoozer said:**
> Have both Windows and Ubuntu installation media handy.
Boot into the Windows install DVD and repair the Windows boot loader (an update would not have modified this at all).
Something like this should do it;
```
bootrec /fixboot
``````
bootrec /fixmbr
```Then, [reinstall GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2") to the MBR, not the partition Ubuntu is installed on (ie. sda4 not sda).
I think you mean "sda not sda4".  At least I hope so!

---

### Post by Mr Stoozer on 2011-06-30
> **ajgreeny said:**
> I think you mean "sda not sda4".  At least I hope so!

I do! Thank you.

---

### Post by createdcreature on 2011-06-30
Reinstall.

---

