---
title: "Montaje permanente de dos discos duros"
date: 2009-03-30
forum: New to Ubuntu
---

### Post by Criminel on 2009-03-30
Hola,
Instalé Xubuntu Intrepid Ibex en lo de un amigo, en una máquina de pocos recursos. Tiene dos discos duros. En el principal de 150 GB pusimos el sistema. 
El problema es que el 2do disco (de 60GB) que aparece montado en /media y lo veo cuando le hago un acceso directo al escritorio, se desmonta aleatoriamente y/o cada vez que apagamos la máquina.

¿Cuál es la manera de que quede montado en forma permanente con permisos de lectura y escritura? (para usarlo como backup de datos).

Gracias.

---

### Post by Elfy on 2009-03-30
Hola
and if you want to post in Spanish it might be better to do so on one of the spanish speaking forums - it's likely that there is someone floating about who can speak spanish properly - but not necessarily so in the time it might take to move of page 1 :)

[http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

I think that you are looking to mount a drive on boot - you need to do that with fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Criminel on 2009-03-30
First of all, my apologies. I thought I was on a spanish forum.
To make things shorter:

Xubuntu Intrepid on a friend's machine. We installed the system on disk 1 (150GB) and the second disk appears to be mounted on /media (at least I could create a shortcut somehow, and I see it listed). The problem is that the 2nd disk dissapears each time we turn off the machine and/or randomly.

Any help in mounting this second disk permanently?

many thanks.

---

### Post by Elfy on 2009-03-30
Absolutely - I gave the link above and obviously used babel fish properly :)

In a nustshell you need to make a folder to mount the partition into

```
sudo mkdir /media/name
```

Then you can add the partition to the fstab file - this will then get it mounted each time you boot xubuntu.

If you need further help please, tell what name your friend wants the drive to be named and then run these from a terminal and post the output

```
sudo fdisk -l
blkid
```

---

### Post by Criminel on 2009-03-30
Thanks. I'll check all of the above as soon as I get home.
Just in case, I assume we can give any name to this second disk, right? (let's say,something creative, like "backup"?)

Thanks again.

---

### Post by Elfy on 2009-03-30
Yes - call it anything you wish - bear in mind it appears on the desktop if you use /media, if you don't want it to use /mnt instead 

All you need to remember is that whatever name you use - is the one to use in fstab, so for instance I made a folder /mnt/data and the corresponding fstab entry is

UUID=000cf730-bffc-4ab6-bd8d-3305b4218fcf /mnt/data ext3 defaults,relatime 0 2

---

