---
title: "windos recovers messed up something"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by ninja1182 on 2011-08-14
help meeeeeeeeeee

i have an acer aspire one netbook with hlaf of my hard drive partaton off for windows and the other hlaf with ubuntu i restored my windows with option it gives me in my bootloader for recovery and now my windows says install incomplet when it starts up as it going to the desktop what did i do wrong i need windows for some programs i cant run here

---

### Post by powerpleb on 2011-08-14
> **ninja1182 said:**
> help meeeeeeeeeee

i have an acer aspire one netbook with hlaf of my hard drive partaton off for windows and the other hlaf with ubuntu i restored my windows with option it gives me in my bootloader for recovery and now my windows says install incomplet when it starts up as it going to the desktop what did i do wrong i need windows for some programs i cant run here

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Good luck. :)

---

### Post by Mark Phelps on 2011-08-14
> **ninja1182 said:**
> help meeeeeeeeeee

i have an acer aspire one netbook with hlaf of my hard drive partaton off for windows and the other hlaf with ubuntu i restored my windows with option it gives me in my bootloader for recovery and now my windows says install incomplet when it starts up as it going to the desktop what did i do wrong i need windows for some programs i cant run here

I'm guessing you tried used the Acer-provided option to "restore" your PC to its original condition, right?

Usually, that just works -- but if you damage the Recovery partition, and in some cases, just resize the Win7 partition, the restore can't work properly.

What I would suggest you try is the following:
1) Boot from an Ubuntu desktop PC
2) Select Try Ubuntu -- do NOT install it
3) When you FINALLY get to a desktop (takes a LONG time), use the Disk Utilities to look at the partitions on your drive. If you still have a Recovery partition and you also have one or more Linux partitions, then continue ...
4) Use the Gnome Partition Editor to remove the Linux partitions.
5) NOW, you're likely to have a small boot partition, a Win7OS partition, and a Recovery partition.
6) Reboot and try the Restore again.  It might work this time.

If it still does not work, you will have to contact Acer to get full-recovery disk media from them -- because the builtin restore function doesn't work anymore.

---

### Post by ninja1182 on 2011-08-14
will try to format the linix partation im running xp also dose that have an affect on whats going on here and if that dose not work what would me my next option

---

### Post by Mark Phelps on 2011-08-15
> **ninja1182 said:**
> will try to format the linix partation im running xp also dose that have an affect on whats going on here and if that dose not work what would me my next option

No, the OS doesn't really matter -- the steps are the same.

If you get through step 6) and restore does not work, I already told you what you needed to do then:

> If it still does not work, you will have to contact Acer to get full-recovery disk media from them -- because the builtin restore function doesn't work anymore.

---

