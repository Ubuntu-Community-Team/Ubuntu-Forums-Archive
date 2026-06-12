---
title: "VirtualBox - recommended specs"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by nachos99 on 2009-02-21
i have a desktop running XP right now with the specs below.

Intel Pentium 4 - 3.06GHz
2GB DDR SDRAM
NVidia Quadro NVS - 128MB RAM 
40GB HDD
1TB HDD

im planning on setting up a dual boot with xp/ubuntu.  

what kind of specs are needed/recommended to decently run an XP in a virtual machine in ubuntu?

is my processor too dated?  do i have insufficient RAM?

thanks,

---

### Post by rams123 on 2009-02-21
512MB is enough for XP. But if you run heavy apps (like dreamweaver,fireworks), try 1GB.

---

### Post by konqueror7 on 2009-02-21
virtualbox will automatically recommend you anyway with default settings depending on the OS for the vm...mine is 768ram 64video, needed to run netbeans...but 512 is already enough...

---

### Post by Klaz168 on 2009-02-21
Im running XP on VBox with 512MB of RAM, its running just fine as I dont use any heavy applications.

Please not that, everytime the virtualmachine is started VBox will allocate this much memory from your host machine and present it to the guest operating system.

That basically means, if you have 2GB of RAM, then you assign 1GB to the guest OS (Windows XP), you'll have 1GB left to use on Ubuntu.

I'd recommend adding more RAM if your going to run heavy applications on the host or guest.

---

### Post by DMcA on 2009-02-21
when I installed VirtualBox I accepted the defaults which were something like 192Mb and 8Mb for video. XP runs just fine with this, although I just use it for one or two windows only programs. In fact it ran a lot better than the ubuntu host (although admittedly I only had 512Mb total - I've since upgraded to 1200Mb of RAM)

---

### Post by binbash on 2009-02-21
Slim down the xp with nlite, then 256mb ram is enough.However with nlite + 512 ram, it will be very fast : )

---

### Post by HavocXphere on 2009-02-21
nachos99: Your gear is perfectly fine for what you want to do.;)

If you run into performance issues, then you could always switch of themes on the XP install..then its got a Win2000 look to it.

I'd boost the video mem that Virtual box allocates to 32mb though (default is 12mb I think). And RAM to 512 (default=256). But thats more of a generic thing...not just for your hardware.

---

