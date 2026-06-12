---
title: "Help needed: Boot failed (SRST errno=-16)"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by Zenmij on 2010-08-09
Hi, recently upgraded to 10.04 and seemed to go without a hitch for a day or two until today, I noticed what sounded like me hard drive having problems.

Tried rebooting, and nothing happens for 20 minutes until I get a screen filled with :

> [299.8045820 ata2.00: failed comman: WRITE DMA
0299.8048680 ata2.00: cmd ca/00:08:3f:00:00
                res 40/00:01:00:00:00/40
299.805702] ata2.00: status:  [ DRDY ]
319.844028] ata2: SRST failed (errno=-16)
329.856031] ata2: SRST failed (errno=-16)
364.900027] ata2: SRST failed (errno=-16)


Anyone know what is going on?

Many Thanks.

---

### Post by jtarin on 2010-08-09
Put the 10.04 disk back in, boot to it, and then use the command

```
sudo touch /forcefsck
```
and restart. The system will run a standard disk check on boot up. That may solve problems, but you can also use the System ->Administration ->Disk Utility and see if that finds anything. I would consider a backup at this point if you can boot, as in all probability its a hard drive problem.

---

### Post by Zenmij on 2010-08-23
Thanks - I have had no problems with this since.

---

