---
title: "Cant install encore ethernet adapter enl832-tx-icnt"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by puedovolar on 2007-09-25
Hi. I recently switched to linux and tried to install ubuntu on an old computer. Im really having trouble installing the drivers of the LAN adapter to get my internet working. Could someone help me out please?
Ive got the floppy, with the drivers in a folder named linux. I copied the whole linux folder to my desktop and then wrote in terminal (in the drivers directory):

#Make all

as the readme file said.
i think i cant generate neither sundance.ok or sundance.o.  This is the error that shows up:

```
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/tkdepto/Desktop/Fdriver modules
make[1]: Entering directory '/usr/src/linux-headers-2.6.20-15-generic'
    CC [M] /home/tkdepto/Desktop/Fdriver/sundance_main.o
/home/tkdepto/Desktop/Fdriver/sundance_main.c:221: error: expected ')' before string constant
/home/tkdepto/Desktop/Fdriver/sundance_main.c:222: error: expected ')' before string constant
/home/tkdepto/Desktop/Fdriver/sundance_main.c:223: error: expected ')' before string constant
/home/tkdepto/Desktop/Fdriver/sundance_main.c:224: error: expected ')' before string constant
/home/tkdepto/Desktop/Fdriver/sundance_main.c: In function 'netdev_open':
'request_irq' from incompatible pointer type
make[2]: *** [/home/tkdepto/Desktop/Fdriver/sundance_main.o] Error 1
make[1]: *** [_module_ /home/tkdepto/Desktop/Fdriver] Error 2
make[1]: Leaving directory ...
make: *** [all] Error 2
```

thanks. please forgive my english! :?

---

