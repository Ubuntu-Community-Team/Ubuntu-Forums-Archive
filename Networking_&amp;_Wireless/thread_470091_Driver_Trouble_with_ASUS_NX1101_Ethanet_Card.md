---
title: "Driver Trouble with ASUS NX1101 Ethanet Card"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Miss Mika on 2007-06-10
:KS Hey :KS

I just got a new ethanet card. And I can't install the driver. 
There is a linux driver on the driver disc it came with 

at first I got this.

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** No rule to make target `v2.09e'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

Then I sorted the headders but now I'm getting this.

mike@gobshite:~/Linux v2.09e$ sudo make all => generate ipg.ko
make: *** empty variable name. Stop.

Any help would really be appreciated.

Thanks Mika8-[

---

### Post by chili555 on 2007-06-10
It would help to see the actual .tar.gz file. Is it available for download somewhere? Can you please give us the URL? If it is the one from the Asus site, it appears to built for kernel 2.4.x. Ubuntu runs 2.6.x.

Did you try the module built in to your kernel:```
sudo modprobe ipg
```

---

### Post by Braveheart1980 on 2008-01-19
Sorry for digging this subject , but did the "sudo modrpobe ipq" work?

I am consindering buying this card  for my ubuntu box!

---

### Post by fanderss on 2008-02-04
Hi I have the same problem with installing this driver.

And "chili555" as far as I can see there is a section in the makefile for kernel 2.6.x.
I have noticed that I have no "build" folder under  /lib/modules/2.6.22-14-server/ why is that?
In the makefile that folder is referred to so perhaps this is the problem???

:guitar:    //fanderss

---

### Post by chili555 on 2008-02-04
> I have no "build" folder under /lib/modules/2.6.22-14-server/ why is that?Do you have a symbolic link to /usr/src/linux-headers-xxx? Have you installed the headers? Have you installed build-essential?

```
 build -> /usr/src/linux-headers-2.6.22-14-generic
```

Again, I would love to troubleshoot this problem, but I'd need to see the tar.gz file. Can you please let me know where you got it? URL?

---

