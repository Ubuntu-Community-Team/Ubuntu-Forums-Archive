---
title: "cant install ess_2.6-v0.4 modem driver on 8.10"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by nemanaldin on 2008-11-18
hi 
i installed ubuntu 8.10 and want to install my modem creative ess 125d 2898 driver ( ess_2.6-v0.4 ) but when i want compile the driver it give me error
what can i do? 
i use this driver on ubuntu 8.04 
i put error here for u from make.log
```
  LD	binary.a
make -C /lib/modules/2.6.27-7-generic/build M=/home/nemanaldin/ess_2.6-v0.4
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  LD      /home/nemanaldin/ess_2.6-v0.4/built-in.o
  CC [M]  /home/nemanaldin/ess_2.6-v0.4/essserial-2.6.o
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c: In function â€&#1705;ess_interruptâ€™:
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:150: error: storage size of â€&#1705;i387â€™ isnâ€™t known
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:150: warning: unused variable â€&#1705;i387â€™
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:164: error: invalid lvalue in asm output 0
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:171: error: memory input 0 is not directly addressable
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c: In function â€&#1705;esscom_do_timer_tickâ€™:
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:199: error: storage size of â€&#1705;i387â€™ isnâ€™t known
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:199: warning: unused variable â€&#1705;i387â€™
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:206: error: invalid lvalue in asm output 0
/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.c:212: error: memory input 0 is not directly addressable
make[2]: *** [/home/nemanaldin/ess_2.6-v0.4/essserial-2.6.o] Error 1
make[1]: *** [_module_/home/nemanaldin/ess_2.6-v0.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [all] Error 2

```  
thanks

---

### Post by nemanaldin on 2008-11-18
no one can help?

---

### Post by helmut_hed on 2008-11-18
Hi Nemanaldin,

Unfortunately the ESS driver has not yet been updated for Ubuntu 8.10.  I'm sorry but it will take some time (a few weeks?) as I am busy with work.  I apologize for the delay.

Best Regards,
Jeff

---

### Post by nemanaldin on 2008-11-19
thanks jeff for ur attention
i will wait for your update
best regards

---

### Post by helmut_hed on 2009-01-07
For anyone else who sees this, the new driver may be found here:

[http://tx.technion.ac.il/~raindel/ess_2.6-v0.5.tar.gz](http://tx.technion.ac.il/~raindel/ess_2.6-v0.5.tar.gz)

It supports 8.10 Intrepid.

For some reason I cannot edit the "HOWTO" anymore...

---

### Post by xt-lee on 2009-05-13
I'm running this on ubuntu 9.04. The modem has trouble sending faxes. They are interrupted with some carrier error.

I'd like to try another modem. How do I uninstall this driver?

---

### Post by helmut_hed on 2009-05-13
Just do "sudo make uninstall" in the build directory.

---

