---
title: "Compiling SiS900 Network Driver"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by groonrix on 2010-07-01
Hi.
My Internet connection seems to be extremely slow.
I dual-boot, and installing a SiS900 driver solved the problem at Win XP.
Now I want to do the same thing in Ubuntu, but only source code is available.
I've never installed a driver from source before, can you help me?
 
Here is the attached readme:
 
"make modules" fails on Redhat 8.0.It is kernel 2.4.18-14 , and it need driver 1.08.06.
You can individually compile the sis900.o with below procedures: 
a.Symbolic Links "asm" and "linux" to "/usr/src/linux-2.4.18-14/include/." 
a.1.Go to /usr/include directory 
a.2.mv asm asm_ ( or rm asm) 
a.3.mv linux linux_ (or rm linux) 
a.4.ln -s /usr/src/linux-2.4.18-14/include/asm asm 
a.5.ln -s /usr/src/linux-2.4.18-14/include/linux linux 
b.Create new directory and copy sis900.c and sis900.o into them. 
b.1 mkdir tmp 
b.2 cp -f sis900.c /tmp/sis900.c 
b.3 cp -f sis900.h /tmp/sis900.h 
b.4 cd /tmp 
b.5 gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -o6 -c -sis900.c 
c.Copy and replace sis900.o into "/lib/modules/2.4.18-14/kernel/drivers/net/." 
c.1 cp -f sis900.o /lib/modules/2.4.18-14/kernel/drivers/net/sis900.o 
 
Is there an easier way?
Plus, the driver seems to be from 2006, is it still compatible with the kernel?

---

### Post by cariboo on 2010-07-01
There has been an sis900 module included for years with the kernel, there is no need to compile an older driver. I've used it with no problems. If you are experiencing slow transfer speeds, your problem may be elsewhere.

---

### Post by sandyd on 2010-07-01
> **groonrix said:**
> Hi.
My Internet connection seems to be extremely slow.
I dual-boot, and installing a SiS900 driver solved the problem at Win XP.
Now I want to do the same thing in Ubuntu, but only source code is available.
I've never installed a driver from source before, can you help me?
 
Here is the attached readme:
 
"make modules" fails on Redhat 8.0.It is kernel 2.4.18-14 , and it need driver 1.08.06.
You can individually compile the sis900.o with below procedures: 
a.Symbolic Links "asm" and "linux" to "/usr/src/linux-2.4.18-14/include/." 
a.1.Go to /usr/include directory 
a.2.mv asm asm_ ( or rm asm) 
a.3.mv linux linux_ (or rm linux) 
a.4.ln -s /usr/src/linux-2.4.18-14/include/asm asm 
a.5.ln -s /usr/src/linux-2.4.18-14/include/linux linux 
b.Create new directory and copy sis900.c and sis900.o into them. 
b.1 mkdir tmp 
b.2 cp -f sis900.c /tmp/sis900.c 
b.3 cp -f sis900.h /tmp/sis900.h 
b.4 cd /tmp 
b.5 gcc -DMODULE -D__KERNEL__ -Wall -Wstrict-prototypes -o6 -c -sis900.c 
c.Copy and replace sis900.o into "/lib/modules/2.4.18-14/kernel/drivers/net/." 
c.1 cp -f sis900.o /lib/modules/2.4.18-14/kernel/drivers/net/sis900.o 
 
Is there an easier way?
Plus, the driver seems to be from 2006, is it still compatible with the kernel?
a) the driver is not compatible with the current version of ubuntu
b) see above post.

---

### Post by groonrix on 2010-07-02
Thanks for your replies.
As mentioned, I experienced the problem in both operating system,
which I solved in XP by updating the driver.
Any idea what might cause that problem in Ubuntu?

---

