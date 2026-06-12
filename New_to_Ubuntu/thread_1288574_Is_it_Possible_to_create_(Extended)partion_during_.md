---
title: "Is it Possible to create (Extended)partion during new Install???"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by kaymac on 2009-10-11
Ubuntu 9.04 installation.

Hi Everyone,

Its my first post and my first run at Ubuntu, so bear with me.

Im installing Ubuntu from your cd onto a ready made partition.
I already had a partition ready for the installation but didnt realise Id need another for the swap file.(I already have 4 partitions)
Is it possible to create a logical extended partitian during installation and if so how?

or

Am i better off returning to my os and fix the partition there first?

(I searched for a similar thread and the manual but couldnt find an answer).

Thanks all,
kaymac

---

### Post by LewRockwell on 2009-10-11
use the LiveCD and partition editor to get your partitions the way you want them BEFORE installation

.

---

### Post by falconindy on 2009-10-11
GParted is loaded and is almost fully available during the install process. There's no need to boot off the LiveCD before installing. When you're prompted to pick an install location, request to specify your partitions manually.

If you want to fix it after the install, you can easily shrink an existing partition and add in a swap (via GParted).

---

### Post by LewRockwell on 2009-10-11
or you can just boot up a distro and bash it out with fdisk and/or cfdisk

.

---

### Post by kaymac on 2009-10-11
[I][COLOR="Blue"][QUOTE=LewRockwell;8088341]use the LiveCD and partition editor to get your partitions the way you want them BEFORE installation.
[/COLOR][/I]

*[COLOR="SeaGreen"][COLOR="Blue"][QUOTE=Falconindy;8088342]GParted is loaded and is almost fully available during the install process. There's no need to boot off the LiveCD before installing. When you're prompted to pick an install location, request to specify your partitions manually.[/COLOR]*[/COLOR]


:P)Thanks guys.

 I wasnt 100% what was best so I used a disk manager I had on vista. I created a partition with an extended partition.
The bigger was for Ubuntu OS(24gb) and the smaller(4gb)as the swap file/partition.
I selected the file systems for both but ***didnt*** format there and then.
On Reboot: I just had to 'manually' prepare a partition, this took seconds as it was ready, the extended partition became the swap file.
Only had to format the OS partition, took 15 minutes then installed UBuntu perfectly.)

BTW for any other first timers, 
I set the partiton to simply U:/  ie. 
Drives -A:  (Windows)
       -B:   (Windows)
       -C:     (back ups)
      [COLOR="rgb(46, 139, 87)"] -**U:/**
 [INDENT[/INDENT]--EXT.Partition P:    (swap)[/COLOR]

On reboot it gave me the choice to boot from Vista or Ubuntu, booted from Ubuntu and its running great.

Thanks to LewR & Falconindy for their advice ::P
Kaymac

---

