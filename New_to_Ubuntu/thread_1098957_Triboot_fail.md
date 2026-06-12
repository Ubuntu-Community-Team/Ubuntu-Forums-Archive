---
title: "Triboot fail"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by .Fuze on 2009-03-17
Well I realize it was rather a mistake now, however I attempted to triboot; Vista, Sabayon, as well as Ubuntu.

However the problem is not with Vista or Sabayon, dualbooting they both worked fine.. When I installed Ubuntu last night, Vista as well as Sabayon do not show up on the GRUB loader.

I already examined everything I could from using
```
fdisk -l
```
yet even in /boot/grub/menu, there was no knowledge of Vista or Sabayon.

Any tips on getting Vista and Sabayon back?


Thank you,

**Fuze**

---

### Post by Jose Catre-Vandis on 2009-03-17
First find out where all your OS's are installed
```
sudo gparted
```
examine the files systems to determine the locations of Vista and Sabayon. Lets assume Vista is on hda1/sda1 (hd0,0) and Sabayon is on hda2/sda2 (hd0,1).

Next mount the Sabayon partition:
```
sudo mkdir /media/Sab
sudo mount /dev/sda2 /media/Sab
```
Now you can browse to the sabayon /boot/grub/menu.lst and copy the default entry to boot Sabayon.

Let's try some editing of your menu.lst file in ubuntu:
```
sudo nano -w /boot/grub/menu.lst
```
Scroll down to the bottom and add:

The entry you copied for sabayon, then:

```
title         "Windows Vista"
root         (hd0,0) # or (sd0,0) for SATA drive:default ubuntu?
chainloader      +1
```

save out your menu.lst and reboot.

Does it work?

---

### Post by .Fuze on 2009-03-17
Unfortunately 'gparted' isn't working :\


Edit: brb, live cd.

---

### Post by .Fuze on 2009-03-17
[IMG]http://i41.tinypic.com/x2nv35.png[/IMG]

[IMG]http://i42.tinypic.com/idvlns.png[/IMG]

For some reason I don't have a great feeling about this

---

### Post by Volt9000 on 2009-03-17
Hmm, I may just be a noob but I don't think you can mount sda2 directly since it's an extended partition containing other partitions. Besides, the partition contained within appears to be a swap partition.

Is /dev/sda your main Linux partition? Do you have any other physical drives in the system?

---

### Post by .Fuze on 2009-03-17
The thing is that sda1 should be Vista, but it's not, it's Ubuntu. This is my only HD, what it looks like is that Ubuntu may have wiped out my memory? If that's possible.

I'll be honest, I really have no idea what happened, all I know is Vista and Sabayon were installed, I installed Ubuntu last night, checked when I woke up, was all successful, rebooted then to my dismay there was no longer Vista or Sabayon on my GRUB.

---

### Post by bagle on 2009-03-17
just a sugestion  but you might have slipped and deleted the windows and sayboyn partitons while you were useig the live cd.;)

---

### Post by Botbob89 on 2009-03-17
I just want to applaud you for your ambition :D

Good luck fixing it though, it seems you have managed to lose parts of Windows as bagle said.....

---

### Post by .Fuze on 2009-03-18
Woot!

So now here's the question.. Did I lose all my files? :D

---

### Post by clive littlewood on 2009-03-18
Hi

I,m afraid it appears that when you installed Ubuntu you must have "chosen" to install "using whole disc".

I would suggest you do not touch anything on the partition as others might be able to suggest some program to recover your data.

Clive

Backup > Backup then Backup again

---

### Post by .Fuze on 2009-03-18
> **clive littlewood said:**
> Hi

I,m afraid it appears that when you installed Ubuntu you must have "chosen" to install "using whole disc".

I would suggest you do not touch anything on the partition as others might be able to suggest some program to recover your data.

Clive

Backup > Backup then Backup again

Thank you for helping understand what happened, as I didn't pay much attention while installing.



News! I managed to take ubuntu off for now while erasing then writing it over with Sabayon, so now when checking my partitions, I have a 220gb partition but it does not have a format, ie: SDA1 is Sabayon, SDA2 is unknown.

Should it be NTFS? Or EXT1? :\


Thanks for the replies guys.

---

