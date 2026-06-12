---
title: "cd/dvd still on desktop after manually ejecting"
date: 2011-02-26
forum: New to Ubuntu
---

### Post by shy.guy on 2011-02-26
hello, this is my first post here. i'm using 10.10 maverick in an acer aspire laptop. my problem is whenever i manually eject a cd or dvd it remains mounted on desktop as if nothing has happened. i believe this problem has something to do with another one: the fact i can't burn cds with brasero. in the final step, when the cd should eject itself, it gives an error message asking me to manually eject the cd to complete the burning, but that's impossible because when i eject it, it's still mounted and the message doesn't go away. one last detail: i can normally eject cds and dvds that are already burned or originals by right clicking >>> eject.

---

### Post by shy.guy on 2011-02-26
uhh..anybody?

---

### Post by Hedgehog1 on 2011-02-26
> **shy.guy said:**
> hello, this is my first post here. i'm using 10.10 maverick in an acer aspire laptop. my problem is whenever i manually eject a cd or dvd it remains mounted on desktop as if nothing has happened. i believe this problem has something to do with another one: the fact i can't burn cds with brasero. in the final step, when the cd should eject itself, it gives an error message asking me to manually eject the cd to complete the burning, but that's impossible because when i eject it, it's still mounted and the message doesn't go away. one last detail: i can normally eject cds and dvds that are already burned or originals by right clicking >>> eject.

For now, you will need to right click on the icon and select 'eject'.

There is a bug report for this: 

[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/476654]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/476654")

They were having trouble reproducing this defect (according to the log) as it seems to be rather hardware specific.

My CD/DVD/Blu-Ray burner also do not physically eject after a burn of a disk.  It has, however, ejected when Ubuntu told it to on a few other occasions (and startled me).

Are you running the 64 bit or 32 bit Ubuntu? This was originally reported against the 64 bit version.

---

### Post by Hedgehog1 on 2011-02-26
shy.guy,

Can you tell if your CD/DVD unit is IDE (PATA) or SATA?

I see that 10.10 loads a package called 'eject', but the description is it supports IDE/atapi drives.

My drive CD/DVD is a SATA - if yours is too that may be a place to start figuring this out.

:KS

---

### Post by shy.guy on 2011-02-27
my drive is IDE and i'm running 32 bit version. thanks for the reply.

---

### Post by Hedgehog1 on 2011-02-27
> **shy.guy said:**
> my drive is IDE and i'm running 32 bit version. thanks for the reply.

Thanks - so we know it happens on 32 and 64 bit versions, and on both IDE and SATA CD/DVD drives.

I am hoping to find out more and report either:

1) A bug
2) A setup/install change

It could be a while, but it is an interesting problem. :P

---

### Post by Hedgehog1 on 2011-03-06
shy.guy,

We have a working solution for the eject on SATA CD/DVD/BluRay drives.

Here is the link to the new thread:

[Eject on SATA CD/DVD drive not working]("http://ubuntuforums.org/showthread.php?p=10530864#post10530864")

As best as I can tell, this solves everything except:

*'When manually ejecting a SATA CD/DVD using the button on the drive, the CD/DVD ejects, but CD/DVD drive does not unmount like an IDE drive does'.*

***The Hedge***

:KS

---

