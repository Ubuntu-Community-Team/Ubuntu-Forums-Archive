---
title: "How do I force a file system check in Intrepid Ibex?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by s.fox on 2009-03-11
Hi,

I would like my system to perform a file system check in Intrepid Ibex.   The command below doesn't seem to be supported in 8.04.

```
shutdown -rF now

```

Google has been pretty much useless.  

Thanks for any help.

Ash R

---

### Post by Eisenwinter on 2009-03-11
Do you mean you want to check your filesystems every boot before they're mounted?

Look into the fsck command, and the file /etc/rc.local

---

### Post by philinux on 2009-03-11
> **Ash R said:**
> Hi,

I would like my system to perform a file system check in Intrepid Ibex.   The command below doesn't seem to be supported in 8.04.

```
shutdown -rF now

```

Google has been pretty much useless.  

Thanks for any help.

Ash R

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by s.fox on 2009-03-11
Hi,

Something like every 30 boots Ubuntu performs some sort of system check.  I want to perform one of these checks.

Thank you

---

### Post by LegendofTom on 2009-03-11
I think the program is called tune2fs, so try the man pages.

---

### Post by s.fox on 2009-03-11
Hi,

I got it sorted using fsck.  

Thank you everyone for the help.

---

### Post by oldos2er on 2009-03-11
Boot into recovery mode; fsck should be one of the menu options.

---

### Post by s.fox on 2009-03-14
Hi again,

I think this may have back fired on me.   Now I my computer is running a system check EVERY time I boot up.  I assume its something to do with the fact that I have created the folder "forcefsck" following [this]("http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/") guide.

Would it be advisable just to delete this folder or would this in itself cause problems?  Some direction would be much appreciated.

Many thanks.

-Ash R

---

### Post by pakmor on 2009-03-14
I find it easier to have the file system checked by using "sudo touch /forcefsck" then the next time only your file system is checked before anything is mounted.

---

### Post by s.fox on 2009-03-15
I have fixed it. :D

I ran the scan in the recovery mode.  That seems to have sorted it out as I have booted and rebooted several times now without the system performing a scan.  :D

Once again,  thank you to everyone for the input.

-Ash R

---

