---
title: "Backup"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by OwNeD on 2009-11-24
How can i backup my whole filesystem and CD/DVD drive ?  is there anything else i should backup other then the whole filesystem folder and cd/dvd drive? i knowh one command that backups everything on the computer.. but thats not what i want.. 



- Thanks

---

### Post by jbrown96 on 2009-11-24
You shouldn't backup your entire filesystem. There are folders like /dev, /proc/, /sys that are not really part of your filesystem. They are created every time you boot the computer. Therefore, you don't want to back them up. You can use the -x flag in cp to only backup the real file system. You will need to run another command to backup your CD.

---

### Post by scorp123 on 2009-11-24
> **OwNeD said:**
> How can i backup my whole filesystem 

[http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a](http://forums.linuxmint.com/viewtopic.php?f=42&t=3969&start=0&st=0&sk=t&sd=a)

---

### Post by Ampi on 2009-11-24
You can also install the program SBackup (Simple Backup) which has different options for backup. It has also a nice simple GUI and there is enough to be found on the internet, just google it or ubuntu it :).
Then you make your backups as customizabled as you want..
Hope it helps :)

---

