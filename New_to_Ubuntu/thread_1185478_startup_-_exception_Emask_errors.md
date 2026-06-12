---
title: "startup - exception Emask errors"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by poisonborz on 2009-06-12
Hola,

I tried to install 9.04 today, but both the livecd and the later the installed OS gave long messages like this:

```
[28990.792050] ata1.00: exception Emask 0x0 SAct 0xff SErr 0x0 action 0x6 frozen
[28990.792065] ata1.00: cmd 60/80:00:00:4f:ae/00:00:07:00:00/40 tag 0 ncq 65536 in
[28990.792068] res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[28990.792073] ata1.00: status: { DRDY }
```

I first thought it's an error, but everything got on perfectly. However, the start-up time is horribly long like this. I found a similar thread: 

[http://ubuntuforums.org/showthread.php?t=1178006](http://ubuntuforums.org/showthread.php?t=1178006)

The user says nvm fixes it...what is that? Could anyone say what my problem is? My machine has only one ATA disk (so it's no sata error).

---

### Post by Hospadar on 2009-06-12
I think he's saying *nevermind* I fixed it =)

But it looks like some kind of disk/raid issue.

Do you have multiple disks? are they connected in raid?  you might want to try private messaging that guy and ask how he fixed his problem (isn't it nice when people say they fixed a problem, but don't say how?)

Edit:
There's an ubuntu bug report dealing with this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/163637](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/163637)

Sounds like either
a) bad hardware (disk/mobo)
b) wierd kernel/disk controller issue

I suspect b in your case since everything ends up working fine.  You could maybe try a bios update on your mobo (if there is one?)
but depending on the kind of the machine and whether or not you can stand the long bootup, I might say it's safer to just leave it the way it is.

---

### Post by poisonborz on 2009-06-12
No raid, nothing... It's an Abit KX7-333 motherboard, 1.6Ghz AMD cpu, with a single ATA hard drive, 512megs of ram. 

I don't know if it's connected, but somehow the system feels a bit sluggish... Even small operations can hang mouse movement for a bit... could there be problems with disk handling?

---

