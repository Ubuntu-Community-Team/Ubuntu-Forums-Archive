---
title: "Start up menus, several distros"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by OllieGab on 2009-03-16
Decided to install Fedora "next to" Ubuntu but lost the menu of choices of OS at boot up. This was fixed with a live CD and re-installation of the grub, which gave me back my menu. But without the Fedora choice.
Any way to make it show ALL the installed distros on the boot up menu?

And a newbie question; is there a grub specific to each OS?

Cheers Ollie

---

### Post by Vince4Amy on 2009-03-16
Does running:

```
sudo update-grub
```

Add it?

---

### Post by Berserker v7 on 2009-03-16
Grub is not OS specific, although the presently active grub may have entry only for one of the OSes.

You are currently able to access ubuntu right? From ubuntu, mount the fedora partition and open the /boot/grub/menu.lst or /grub/menu.lst (i am not sure of the exact location in fedora) within the fedora partition. then copy the grub entry for fedora from this file. Now open the /boot/grub/menu.lst file in your ubuntu partition and add the previously copied content at the end. that should do the trick.

---

### Post by OllieGab on 2009-03-16
No, same menu as before, just Ubuntu but not the latest installed (Fedora).
I did the grub update command while in Ubuntu, though. Not the live CD....

---

### Post by OllieGab on 2009-03-16
I'm fairly new to Linux...so how do I mount the Fedora partition from within Ubuntu?

---

### Post by philinux on 2009-03-16
Is this a single disk install.

```
sudo fdisk -l
```

There is a menu.lst for each install.

---

### Post by Berserker v7 on 2009-03-16
Can you give a screenshot of file explorer? would really simplify things :)

---

### Post by markbuntu on 2009-03-16
What you really should do is have separate grubs for Fedora and ubuntu in their respective partitions and then add a chainload in the boot grub to the other partition's grub.

This is what I added to the end of /boot/grub/menu.lst on my hd0 which is my primary boot drive. Each of these other distros has its own grub which it updates itself. This avoids a lot of problems that can come up with multiple distros.
 
```

#This entry added to get for 8.04 UnbutuStudio amd64 on sdb

title		Chainload Ubuntu 8.04 amd64
root		(hd1)
chainloader	+1

#This entry added for Mandriva i386 on sdc

title		Chainload Mandriva 2009
root		(hd2)
chainloader	+1


#This entry added for Intrepid on sdd

title		Chainload Intrepid
root		(hd3,0)
chainloader	+1

#This entry added for Jaunty on sdd3
title		Ubuntu Jaunty 9.04 kernel 2.28-6-generic
root		(hd3,2)
chainloader      +1

```

When you install other distros have them install their grub in the drive/partition where you installed the distro and just add a chainload entry in the primary boot grub. Believe me, you will save yourself a lot of headeaches if you do it this way.

---

### Post by philinux on 2009-03-16
Or this way.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Whatever's on SDB
configfile   (hd1,0)/boot/grub/menu.lst
```

---

### Post by markbuntu on 2009-03-16
That makes an assumption that there is a /boot/grub/menu.lst on SDB. Chainloader can load windoze or macOS. It can load anything with a boot sector, no matter what it is. It is the fire and forget of grub.

---

### Post by philinux on 2009-03-16
I was using this as an **example **for linux.
Hope this helps anybody else.
[http://ubuntuforums.org/showthread.php?t=724817&highlight=configfile](http://ubuntuforums.org/showthread.php?t=724817&highlight=configfile)

---

