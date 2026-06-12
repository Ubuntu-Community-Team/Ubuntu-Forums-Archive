---
title: "How to undelete Ubuntu 11.04 (dual boot XP)"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by nichos on 2011-07-16
I dualboot Ubuntu in 3 home systems but want it out of one PC.

I read of deleting its partition & use XP Repair Console to boot XP but, once I had to reformat because I did not have the Admin password.

Is there a safer way tu unistall Linux?

I found the XP Boot.ini, if I edit out the Ubuntu reference will this take it out?
".........[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"........"

I looked into "grub" but is too complicated.

How about Wubi, does it uninstall?

Thanx ....nick

---

### Post by westie457 on 2011-07-16
> **nichos said:**
> I dualboot Ubuntu in 3 home systems but want it out of one PC.

I read of deleting its partition & use XP Repair Console to boot XP but, once I had to reformat because I did not have the Admin password.

Is there a safer way tu unistall Linux?

I found the XP Boot.ini, if I edit out the Ubuntu reference will this take it out?
".........[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"........"

I looked into "grub" but is too complicated.

How about Wubi, does it uninstall?

Thanx ....nick

Take a look at this 

[http://ubuntuforums.org/showthread.php?t=861983](http://ubuntuforums.org/showthread.php?t=861983)

It is an old one. The principles are the same.

---

