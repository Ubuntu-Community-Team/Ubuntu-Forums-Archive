---
title: "Installing Ubuntu 9.04 in second hard disk"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by joe2005 on 2009-09-15
I want to install Ubuntu 9.04 on my second hard drive for which Partition L reserved.Windows RC is on the first partition K.Windows XP is on the first hard drive C.I want to know how to make the installation is done on L.

---

### Post by katakaio on 2009-09-15
When you perform the Ubuntu installation, you will be asked which hard drive you want to install Ubuntu on. When given a list of partitioning methods, select *manual* and you'll be able to see each hard drive and the partitions that are set up on each. Select the partition that you want to install Ubuntu on, and you're ready to go!

---

### Post by mikeyphi on 2009-09-15
Here's a guide:
[http://linux.host22.com/1_5_Getting-started.html](http://linux.host22.com/1_5_Getting-started.html)

Look at this section titled "Installing Type 2 alternate install (installing to partition or Virtual)"

---

### Post by LewRockwell on 2009-09-15
you might end up with bootloader issues and there are guides and tutorials on bootloaders strewn across the interwebs already so we won't add another

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by joe2005 on 2009-09-15
I started installing Ubuntu and came to partitioning spaces and took the third option of manual and came up with the message"No root file system is defined please correct this from partitioning menu" hope to get guidance thanks

---

### Post by Cypher1101 on 2009-09-15
I'm not sure how far into the installer you were when you got that message. Had the partioner just loaded, or were you at the part where you are able to name and define partitions?

---

### Post by Geoff918 on 2009-09-15
Quick note: While you're installing this, you may want to pull the cable out of your first hard disk drive so that you don't wind up modifying the boot sector on that drive.

I hope you have reviewed some information on this before doing what you're doing because you could create a messy headache for yourself pretty quickly. Which is fine if you like to fix things. I do, so I don't worry about 'em.

---

### Post by joe2005 on 2009-09-15
Thanks for the help.I have finally able to install Ubuntu.There was a small hiccup in that when configuring apt at 83% the system hanged.After vigorous tapping enter key completed install.Will come back with more questions later.thanks

---

### Post by katakaio on 2009-09-16
> **joe2005 said:**
> After vigorous tapping enter key completed install.

I prefer using a hammer, but that works too :P

---

