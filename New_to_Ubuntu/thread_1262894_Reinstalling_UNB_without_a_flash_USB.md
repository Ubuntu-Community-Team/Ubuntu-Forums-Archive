---
title: "Reinstalling UNB without a flash USB"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by Zlash on 2009-09-10
Hey guys.

I currently have an Aspire One Notebook with a Samsung exsternal Dvd USB drive.

I installed ubuntu with it, but i want ubuntu netbook remix due to the better support for small laptops.

I currently only have a 512mb USB disk (the file is about 1g) and i tried installing it on a dvd disk but it wont reqonize it.

---

### Post by Zlash on 2009-09-10
> **Zlash said:**
> Hey guys.

I currently have an Aspire One Notebook with a Samsung exsternal Dvd USB drive.

I installed ubuntu with it, but i want ubuntu netbook remix due to the better support for small laptops.

I currently only have a 512mb USB disk (the file is about 1g) and i tried installing it on a dvd disk but it wont reqonize it.

Anyone? ://

:(

I just burned a second dvd with ubuntu-netbook-remix.img but as soon as the disc is burned the dvd is reqonized as empty and it wont read the freggin thing. 

am i doing something wrong? are you suppose to unfold it like a winrar archive?

gah [www.ubuntu.com](www.ubuntu.com) should add an iso file of netbook remix too :/

---

### Post by NightwishFan on 2009-09-10
You could install using the alternate CD, choose only a command line system, and then manually install the Ubuntu Netbook Remix using:

```
sudo apt-get install ubuntu-netbook-remix
```

Now I have no idea if you want the **lpia** architecture or not. I am not sure how that works, so someone else can clarify.

---

### Post by Zlash on 2009-09-10
> **NightwishFan said:**
> You could install using the alternate CD, choose only a command line system, and then manually install the Ubuntu Netbook Remix using:

```
sudo apt-get install ubuntu-netbook-remix
```Now I have no idea if you want the **lpia** architecture or not. I am not sure how that works, so someone else can clarify.

I need a new clear install to get the drivers and stuff i need. I mounted the Ubuntu Netbook Remix 4 diffrent ways on 4 identical dvds using ubuntu 1 of the times and windows (other c) the other 3 times. non of them works, with the ubuntu install i changed it to an iso and burned it to an empty dvd with ubuntu. after burning i simply get a message saying "invalid mount option when attempting to mount the volume".

altho my pc would run alot better with the netbook remix im almost at the point in which i dont rly care for it. ive used 6 dvds and a full day to try and install the freggin file. just dont understand why it doesnt work. flash img files cant just be turned into an iso maybe?

on btjunkie.org i found a couple of Ubuntu Netbook Remix iso torrents at around 1200mb. think these would be valid usses? if so il download them straight away.

Thanks for the reply. been w8ing! :)

//Z

---

### Post by Chronon on 2009-09-10
I believe you could also use ccd2iso to convert the .img to .iso before burning to disk.

---

### Post by Zlash on 2009-09-10
> **Chronon said:**
> I believe you could also use ccd2iso to convert the .img to .iso before burning to disk.

zlash@Zlash-laptop:~$ ccd2iso '/home/zlash/Desktop/UNR.img' '/home/zlash/Desktop/UNR2.iso'

Unrecognized sector mode (0) at sector 0!

:o

---

### Post by ugm6hr on 2009-09-10
> **Zlash said:**
> I installed ubuntu with it, but i want ubuntu netbook remix due to the better support for small laptops.

NBR is designed to be installed from USB.  Rather than wasting DVD-Rs, either just invest in a (cheap) 1GB+ USB flash, or install the netbook interface on to your existing Ubuntu.

NBR does not have better support for small laptops at all.  The only difference is that is has fewer default applications (to keep the HD footprint small), and it has the netbook interface and maximus.

Just keep your existing installation, and install the remix on top:

```
sudo apt-get install ubuntu-netbook-remix
```

Then reboot.

---

### Post by DoctorLard on 2009-09-10
Not sure where you got your img file from, but the Netbook Remix ISO images are available in the usual places:

[http://cdimage.ubuntu.com/releases/9.04/release/](http://cdimage.ubuntu.com/releases/9.04/release/)
[http://cdimage.ubuntu.com/releases/9.10/alpha-5/](http://cdimage.ubuntu.com/releases/9.10/alpha-5/)

---

### Post by Zlash on 2009-09-11
i have been told ubuntu netbook remix has some atom proccessor upgrades for running more smoothly on netbooks/small laptops

---

### Post by ugm6hr on 2009-09-11
> **Zlash said:**
> i have been told ubuntu netbook remix has some atom proccessor upgrades for running more smoothly on netbooks/small laptops

Nope. You've been misled.

There *is* an lpia kernel available, which is the default kernel for the Dell Ubuntu remix, but it is not the default on the NBR.

---

