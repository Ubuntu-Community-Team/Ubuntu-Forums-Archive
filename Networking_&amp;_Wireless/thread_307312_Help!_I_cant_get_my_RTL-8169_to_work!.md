---
title: "Help! I cant get my RTL-8169 to work!"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by lampemand on 2006-11-26
Ok, I'm know close to nothing when it comes to Linux, just wanted to install it on a laptop i have laying around.

It's an Intel 915GM chipset.

First I tried to install WinXP, I installed the latest driver supplied by the laptop-manufacturer.

In XP it said that "the device is working properly", but I couldn't get on the net or anything, all settings were correct, and it did recieve and send packets (don't know where though).

So I installed the latest Ubuntu, it recognises the card and I can see that it's sending and recieving loads of packets, but I simply can't connect to anything. 

If I plug a wireless card into the laptop then it's all sweet.

Then, I downloaded the driver from the Realtek site (r1000 v1.04) for the 2.6.x kernel (which I have some kind of version of). But when I try "make clean modules" it only gives me this error message:

What is this? Have they forgotten to include some ")"'s in their work? 

I've spent several hours googling, pulling my hair out and what not, but I can't solve this extremely annoying problem! 

It's like having this really fast car but you don't know how to fill it up with gas. :mad:

---

### Post by lampemand on 2006-11-26
Sorry I forgot the error message:

lampe@gurka:~/Desktop/r1000_v1.04$ make clean modules
make -C src/ clean
make[1]: Entering directory `/home/lampe/Desktop/r1000_v1.04/src'
rm -f *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags
make[1]: Leaving directory `/home/lampe/Desktop/r1000_v1.04/src'
make -C src/ modules
make[1]: Entering directory `/home/lampe/Desktop/r1000_v1.04/src'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/lampe/Desktop/r1000_v1.04/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/lampe/Desktop/r1000_v1.04/src/r1000_n.o
/home/lampe/Desktop/r1000_v1.04/src/r1000_n.c:51: error: expected ‘)’ before string constant
make[3]: *** [/home/lampe/Desktop/r1000_v1.04/src/r1000_n.o] Error 1
make[2]: *** [_module_/home/lampe/Desktop/r1000_v1.04/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/lampe/Desktop/r1000_v1.04/src'
make: *** [modules] Error 2
lampe@gurka:~/Desktop/r1000_v1.04$

---

