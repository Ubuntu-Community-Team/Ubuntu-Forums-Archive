---
title: "help me with grub, i cant boot my ubuntu."
date: 2010-01-09
forum: New to Ubuntu
---

### Post by pepe machine on 2010-01-09
guys please help me here... i have successfuly installed ubuntu karmic inside my windows 7. After an update, i restarted it.. but it didnt boot ubuntu.. instead it shows grub's command line.. what should i do? all of my java projects/programs is in there.. i need to get it... 

please, i need to get my java projects, its really important...:(

---

### Post by warfacegod on 2010-01-09
Try typing startx hit enter.

---

### Post by pepe machine on 2010-01-09
> **warfacegod said:**
> Try typing startx hit enter.

didnt work..

---

### Post by pepe machine on 2010-01-09
any idea guys?? please help me..

---

### Post by sandyd on 2010-01-09
searching is believing
[http://ubuntuforums.org/showthread.php?t=1342877](http://ubuntuforums.org/showthread.php?t=1342877)

a good idea is to partition the hard drive instead of using wubi.

---

### Post by warfacegod on 2010-01-09
Do each line one at a time being careful of spelling and spacing.

Example: set Path=/ubuntu/disks/root.disk  *hit Enter, Return, your brother*

Type this at "grub sh>" prompt:

```
set Path=/ubuntu/disks/root.disk
search -f --set=Root ${Path}
probe -u (${Root}) --set=UUID
linux /vmlinuz root=UUID=${UUID} loop=${Path} ro
initrd /initrd.img
boot
```

Once booted in Wubi, open a terminal and type

```
sudo update-grub
```

---

### Post by warfacegod on 2010-01-10
[http://ubuntuforums.org/showthread.php?t=1377175]("http://ubuntuforums.org/showthread.php?t=1377175")

See post #8.

---

### Post by pepe machine on 2010-01-10
> **warfacegod said:**
> [http://ubuntuforums.org/showthread.php?t=1377175](http://ubuntuforums.org/showthread.php?t=1377175)

See post #8.

this fix it.. thank you very much! :D

---

### Post by warfacegod on 2010-01-10
Glad to help.

---

