---
title: "USB-IrDA Kingsun ks-959"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by gzaloprgm on 2007-06-18
Hi there!
I am new to Ubuntu and I have recently installed Ubuntu Edgy on a Desktop Pc. 
All the Hardware was correctly identificated, exeptuating my USB to IRDA adapter.

I searched google linux drivers for it, but I couldn't find anything. 

Is there any driver for it? 

The Model is Kingsun ks-959

Thanks

Gonzalo

---

### Post by floe-de on 2007-07-16
Hi,

I searched for a driver, too. The only thing I found is a patch that is discust in the Linux IrDA Project mailing list
[http://sourceforge.net/mailarchive/forum.php?thread_name=463F5185.6050204%40ceibo.fiec.espol.edu.ec&forum_name=irda-users]("http://sourceforge.net/mailarchive/forum.php?thread_name=463F5185.6050204%40ceibo.fiec.espol.edu.ec&forum_name=irda-users")

So no driver yet...

---

### Post by avillaci on 2007-07-24
Hello, I am the one who wrote the patch mentioned by the URL in the previous response.

To gzaloprgm: you might want to know that I have one of those dongles (KS-959) and I managed to write a Linux driver for it a week ago. You can download it from my homepage: [http://palosanto.com/~a_villacis/]("http://palosanto.com/~a_villacis/"). Previous link of [www.palosanto.com/~a_villacis/](www.palosanto.com/~a_villacis/) is now broken because of a site reorganization..

To install it, you should extract the files inside the tarball, cd into the directory with the files, then run 
make
sudo su -c "make install"

Please tell me if you had success using the driver.

---

### Post by gelax on 2007-08-03
hi.. i have the same problem.....

i need driver for Kingsun KS-959....

( i use xubuntu 7.04)....

thanks :)

---

### Post by avillaci on 2007-08-09
You can check out the driver I wrote at [http://palosanto.com/~a_villacis/]("http://palosanto.com/~a_villacis/"). I also edited a previous post of mine on this thread to correct the URL.

---

### Post by ted_holler on 2007-08-21
I just got my kingsun ks-959 today.

I downloaded and installed your driver without any issues.
I can see that the modules are loaded.

I'm uncertain on which programs I should use to test the driver with.
Can you tell me what program I should use?

Thanks, Ted

---

### Post by imagia on 2008-04-12
> ~/Desktop/ks-959$ sudo su -c "make install"
make -C /lib/modules/2.6.24-16-generic/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/andrew/.local/share/Trash/files/ks-959.2/ks959-sir.o
/home/andrew/.local/share/Trash/files/ks-959.2/ks959-sir.c: In function ‘ks959_probe’:
/home/andrew/.local/share/Trash/files/ks-959.2/ks959-sir.c:712: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/andrew/.local/share/Trash/files/ks-959.2/ks959-sir.o] Error 1
make[1]: *** [_module_/home/andrew/.local/share/Trash/files/ks-959.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [ks959-sir.ko] Error 2

I tried the instructions for installing but the above is what I get. Absolute beginner here, but what am I doing wrong??

Using Hardy x64 if that makes any difference,

---

### Post by bunny rabbit on 2008-05-06
Hey, First thank you avillaci for making this driver. Are you still busy with it?
If you(or anyone else) are:
What does this mean?

make -C /lib/modules/2.6.24-17-generic/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CC [M]  /home/ruben/ks959-sir.o
/home/ruben/ks959-sir.c: In function ‘ks959_probe’:
/home/ruben/ks959-sir.c:712: error: implicit declaration of function ‘SET_MODULE_OWNER’
make[2]: *** [/home/ruben/ks959-sir.o] Error 1
make[1]: *** [_module_/home/ruben] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [ks959-sir.ko] Error 2

I got this in the terminal after I typed: ~$ sudo su -c "make install"
*************************************************************************
Oh hold on. I am trying to send ir signals to my audio receiver. I think I'd better use a more powerful transmitter!
Thanks anyway***

---

### Post by Dino_ on 2008-05-18
I'm having the exact same problem.
Could it be that there needs to be something included that is not present on my ubuntu 8.04 install?

Any help is much appreciated! :-)

> koen@EddyEmmer:~/Downloads/ks-959$ make
make -C /lib/modules/2.6.24-16-generic/build M=`pwd` modules
make[1]: Map '/usr/src/linux-headers-2.6.24-16-generic' wordt binnengegaan
  CC [M]  /home/koen/Downloads/ks-959/ks959-sir.o
/home/koen/Downloads/ks-959/ks959-sir.c: In functie &#8216;ks959_probe&#8217;:
/home/koen/Downloads/ks-959/ks959-sir.c:712: interne fout impliciete declaratie van functie &#8216;SET_MODULE_OWNER&#8217;
make[2]: *** [/home/koen/Downloads/ks-959/ks959-sir.o] Fout 1
make[1]: *** [_module_/home/koen/Downloads/ks-959] Fout 2
make[1]: Map '/usr/src/linux-headers-2.6.24-16-generic' wordt verlaten
make: *** [ks959-sir.ko] Fout 2


---

