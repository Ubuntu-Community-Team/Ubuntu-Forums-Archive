---
title: "partitions question..."
date: 2009-08-04
forum: New to Ubuntu
---

### Post by lems on 2009-08-04
I'm dual booting with vista and ubuntu. Is it possible to reduce the size of the vista partition and give it to ubuntu's partition? If so how?

---

### Post by halitech on 2009-08-04
Should be easy from what I've read but never done it as I don't dualboot.

boot into windows and use the windows partition manager to shrink the windows partition. Make sure you defrag at least twice first. Then boot the Ubuntu live cd and use gparted to expand into the empty space.

Also, is this a true install or a WUBI install?

** Caution -- backup first in case anything goes wrong **

---

### Post by lems on 2009-08-04
i have no idea what a true/wubi install is lol. I'll try what you said.

---

### Post by jacklinux on 2009-08-04
> **lems said:**
> I'm dual booting with vista and ubuntu. Is it possible to reduce the size of the vista partition and give it to ubuntu's partition? If so how?
DO NOT SHRINK VISTA PARTITION!
The corruption change is so HIGH! don't do it!

---

### Post by jacklinux on 2009-08-04
> **lems said:**
> i have no idea what a true/wubi install is lol. I'll try what you said.
wubi installer much safer!: [http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by lems on 2009-08-04
> **jacklinux said:**
> DO NOT SHRINK VISTA PARTITION!
The corruption change is so HIGH! don't do it!

?? didn't i shrink the vista partition to even dual boot? Although... I have to admit that the vista install did screw up, but I was able to restore it(or atleast toshiba was able to restore it :P).

> **jacklinux said:**
> wubi installer much safer!: [http://wubi-installer.org/](http://wubi-installer.org/)

i already have ubuntu installed though :(

---

### Post by jacklinux on 2009-08-04
> **lems said:**
> ?? didn't i shrink the vista partition to even dual boot? Although... I have to admit that the install did screw up, but I was able to restore it(or atleast toshiba was able to restore it :P).
Ah, i though you were going to shrink the vista partition to increase ubuntu's space.
Try wubi for installing. its very good.

---

### Post by halitech on 2009-08-04
if you have the windows install cd, you could always wipe out everything and start over and give windows the amount of room you feel you want and then use the rest of the free space to give ubuntu. Granted this is an extreme way of doing it but *should* be foolproof (I know, build something fool proof and the world produces a better fool)

---

### Post by halitech on 2009-08-04
> **jacklinux said:**
> Ah, i though you were going to shrink the vista partition to increase ubuntu's space.
Try wubi for installing. its very good.

they are already dualbooting so why do a wubi install?

---

### Post by kayvortex on 2009-08-04
As far as I know, shrinking the Vista partition is easy enough to do; but the problem is that the tools that do it are pretty dumb (this was certainly true 6/7 years ago, but I don't know about now). You will certainly have to defrag your Vista partition a few times, but even then you may still end up deleting data in the shrinking process. I usually use opportunities like this to do a fresh install of Windows, but if you do want to go ahead with it, I'd at least back up your important data.

---

### Post by Paddy Landau on 2009-08-04
To shrink a Vista partition:

[LIST=1]
[*]If space is a really big problem, disable System Restore and Pagefile.
[*]Do a full cleanup. Use System Cleanup, and download [CCleaner]("http://www.ccleaner.com/") for extra cleanup.
[*]Do a full defragmentation. The built-in Vista defrag can take a long, long time, so I recommend [Auslogics Defrag]("http://www.auslogics.com/disk-defrag").
[*]Do a full backup! This is important, because sometimes a partition will become corrupted.
[*]Do a Disk Check.
[*]Shrink the Vista partition using Vista's built-in partition manager.
[/LIST]
Ubuntu's gparted can shrink Vista, but unfortunately it has a ***high level of risk with NTFS partitions***, so I strongly recommend that you avoid doing that.

If you can't shrink the Vista partition enough (and that will probably happen), then you need to go to the Microsoft Community Support forums.

---

