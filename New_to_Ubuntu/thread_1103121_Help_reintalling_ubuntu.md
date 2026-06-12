---
title: "Help reintalling ubuntu"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by Geekless freakseeker on 2009-03-22
I've been having some trouble with my ubuntu, and i hope you can help me.

Some guy isntalled in my pc ubuntu + windows xp. I was sooooo happy with my ubuntu, but when i was trying to install some aplication, my ubuntu did't work any more. It seems like a lack of graphic resources. I want to uninstall and then install again muy ubuntu, but i don't know how. I need some help, and you should take into account I'm a begginer, so you should give to me an idiotproof procedure

Gracias, thanks

---

### Post by sandyd on 2009-03-22
hmm... 
what about this...
ill give you all the dierct steps if you run this in the terminal (shows your partitions)
```

sudo fdisk -l

```

i just don't feel like accidentally deleting the wrong partition just becuase i didn't know the partition number ubuntu's on.

---

### Post by kansasnoob on 2009-03-22
As Carlee said we need to know your partition arrangement. The output of:

```
sudo fdisk -l
```

Would give us that. BTW that's a lower case L at the end!

I also wonder though if we can't fix your current installation?

I'd suggest selecting "recovery mode" from the GRUB menu, and once it's done running you'll be presented with a few options:

> resume
dpkg
root
xfix

I'd first select "dpkg - Repair Broken Packgs" and let that run. You'll then be asked to hit enter and you'll see the same list of options.

This time choose "xfix - Try to fix X.....". When that's done it'll again ask you to hit enter and the list again. This time choose to resume normal boot.

You might get lucky! During the "dpkg" process you may be asked if you want to install or remove something, just select (y) or ask here if you're in doubt!

---

### Post by Geekless freakseeker on 2009-03-22
I could't repair my system. It's still running slow.

i don't understand what you mean with <<sudo fdisk>>, i wonder if you saw the word "begginer" in the original thread. The only thing i know is that i have three partitions on my HD. One for windows which is unit C (it's 117 Gb) The other one which seems to have the ubuntu files, It's L and it's 34,7 gb... and the other one (linux swap) U is the smaller with 1,5 gb. I don't know what does it mean the word swap cause i'm from colombia and i speak in spanish so i hope you can help me

---

### Post by kansasnoob on 2009-03-22
Go to Applications > Accessories > Terminal and enter this:

```
sudo fdisk -l
```

That's a lower case L!

We can not tell you how to proceed without knowing the structure of the drive!

---

### Post by kansasnoob on 2009-03-22
I assume you can still boot Ubuntu? If not boot the live CD.

---

### Post by Geekless freakseeker on 2009-03-22
Thank you to the idiotproof explanation. This is what i found out
Disco /dev/sda: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pista, 19929 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x292f292f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       19929    37198507+   5  Extendida
/dev/sda5           15299       19733    35624106   83  Linux
/dev/sda6           19734       19929     1574338+  82  Linux swap / Solaris

---

### Post by Geekless freakseeker on 2009-03-22
> **Geekless freakseeker said:**
> Thank you to the idiotproof explanation. This is what i found out
Disco /dev/sda: 163.9 GB, 163928604672 bytes
255 cabezas, 63 sectores/pista, 19929 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x292f292f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       15298   122881153+   7  HPFS/NTFS
/dev/sda2           15299       19929    37198507+   5  Extendida
/dev/sda5           15299       19733    35624106   83  Linux
/dev/sda6           19734       19929     1574338+  82  Linux swap / Solaris

In case you don't understand, disco means disk, cabezas means heads, sectores I guess means sectors, pista means track, cilindros must be cylinders, unidades = Units, and identificador de disco means Disk Identifyer       
Inicio means... start, begin or something like that, fin means end or finish, Bloques means Blocks, Id means Id and sistema means System.

I'm sorry about the spanish, but it's my language and it was installed by default

---

### Post by blandman3 on 2009-03-22
did you try to run ubuntu in recovery mode?

if you don't know how, here it is:

start computer, choose ubuntu, and then you will come to a screen that has a countdown to enter system menu, or something like that.

After you do that just select ubuntu (recovery) will be in parenthesis.

Then you will come to a screen that has a menu on it.

Choose the "dpkg option" (I don't know what the rest says) but hit enter and press (Y) whenever it asks you to.

This should fix your packages.  Then just choose your option to start normally, should be the first option.  If that doesn't work, let me know............

---

### Post by sandyd on 2009-03-23
> **blandman3 said:**
> did you try to run ubuntu in recovery mode?

if you don't know how, here it is:

start computer, choose ubuntu, and then you will come to a screen that has a countdown to enter system menu, or something like that.

After you do that just select ubuntu (recovery) will be in parenthesis.

Then you will come to a screen that has a menu on it.

Choose the "dpkg option" (I don't know what the rest says) but hit enter and press (Y) whenever it asks you to.

This should fix your packages.  Then just choose your option to start normally, should be the first option.  If that doesn't work, let me know............

scroll up and read the posts.... he did it already....

---

### Post by blandman3 on 2009-03-23
Thanks carlee, I must have been typing that up when I replied because when I started to write it, there was only a couple of threads, and then when I submitted it, well, there were a heck of a lot more--

oh well, can't type fast enough, lol:)

---

### Post by sandyd on 2009-03-23
so lets get you started
got into your BIOS and set the boot sequence to CDROM first

reboot computer

then, stick a ubuntu CD in (8.04 or 8.10, doesn't matter)

go outside and walk for about, lets say 5-10 minutes, depending on your computer's speed

then go click on APplications => ACcessories => Terminal

type in
```

gparted

```
once it opens, carefully! right click on these two partitions, and select delete. (IMPORTANT! MAKE SURE YOUR DELETING THE CORRECT PARTITION!)
```

/dev/sda5 
/dev/sda6 

```
you will need to right click on /dev/sda6 first and select "swapoff"

after clicking "apply", close gparted and go to the desktop

click on "Install"

go through all the steps, their self-explanatory.
When you get to the partitning part, just select "use largest contineous block of free space"(or something close to that)

done!

---

