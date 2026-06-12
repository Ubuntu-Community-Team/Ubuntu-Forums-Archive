---
title: "Asus p5gc-mx/1333 lan don't work"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Escuro Anjo on 2008-08-31
hi ..

it's my first day in ubuntu .. i love it but it can't recognize my lan at all ..

my mother :  Asus p5gc-mx/1333

i download ubuntu version : ubuntu-8.04.1-desktop-i386

works fine but the lan :) ..

please if some one will say some thing please say it in detail :) ..

see you ..

---

### Post by Escuro Anjo on 2008-08-31
please guys it's my first day :) .. i can't do anything because of this ..

---

### Post by Escuro Anjo on 2008-08-31
by the way i have linux lan driver ( from motherboard original CD ) but i don't know what can i do with it :) ..

---

### Post by Escuro Anjo on 2008-09-01
omg !! no answer ?

---

### Post by Escuro Anjo on 2008-09-01
i can't belive this .. really .. this is the offical forum and no answer ?!!!!

---

### Post by deddy on 2008-09-01
> **Escuro Anjo said:**
> by the way i have linux lan driver ( from motherboard original CD ) but i don't know what can i do with it :) ..

I also have the same problem. Please help us.

---

### Post by Escuro Anjo on 2008-09-02
i got a new driver 8/2008 from people.redhat ..

i extract it then i went to terminal ..

i went to the Dir then .. i tried to " make install " but it's answered me : no rule for install " ..

then i tried " make " and the result is :

[PHP]root@ahmed-desktop:~/Desktop/atl2-2.0.5# make
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/root/Desktop/atl2-2.0.5 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_main.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_hw.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_ethtool.o
  CC [M]  /root/Desktop/atl2-2.0.5/atl2_param.o
  LD [M]  /root/Desktop/atl2-2.0.5/atl2.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/Desktop/atl2-2.0.5/atl2.mod.o
  LD [M]  /root/Desktop/atl2-2.0.5/atl2.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
root@ahmed-desktop:~/Desktop/atl2-2.0.5# make install
make: *** No rule to make target `install'.  Stop.
root@ahmed-desktop:~/Desktop/atl2-2.0.5# 
[/PHP]
it biult some files as you can see .. then i tried to " make install " again to make the driver going to " net " folder but i couldn't !!

can anyone tell me what i have to do after this files have shows up ?

thanks ..

---

### Post by fa2f on 2008-09-18
Man, there has been plenty of threads about this LAN card driver -- you should have a search rather than a shout.
Try this: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845)

In short:
> 
1. The driver on CD cannot be used, instead download the new driver: [http://vitriol.ntbti.com/wp-content/uploads/2007/11/attansicl2.tgz](http://vitriol.ntbti.com/wp-content/uploads/2007/11/attansicl2.tgz)
2. Extract and move it to /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko
3. Go to terminal and type in:
insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/atl.ko

You may need root access at step 2 & 3, don't tell me you don't know how to :D

---

### Post by aichis on 2009-11-04
> **fa2f said:**
> Man, there has been plenty of threads about this LAN card driver -- you should have a search rather than a shout.
Try this: [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=429845)

In short:

You may need root access at step 2 & 3, don't tell me you don't know how to :D


how to enable root access??

---

