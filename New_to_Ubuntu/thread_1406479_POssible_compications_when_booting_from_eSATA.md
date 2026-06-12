---
title: "POssible compications when booting from eSATA"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by N4g4rok on 2010-02-14
New to Ubuntu. Wanted to check a couple things before trying to install.

I plan on booting Ubuntu from an eSATA drive, because my Dell laptop will not allow me to partition my internal hard drive. 

I wanted to know if there will be any booting problems if i try to boot my laptop without the eSATA with Ubuntu attached. if so, any way i can avoid those issues?

---

### Post by SlickRick on 2010-02-14
I'm curious as to how your laptop would not allow YOU to partition because last time I checked we [the humans] give the orders to computers.
Jokes aside, if you install Ubuntu on the eSATA, you would not be able to boot from it if you remove it. Seems common sense that you couldn't boot from something that isn't there.
What exactly do you mean by 'without the eSATA with Ubuntu attached'?

---

### Post by N4g4rok on 2010-02-14
If i boot my laptop without the External SATA drive with Ubuntu attached to the computer, does it cause any problems or will it load windows just fine?

and for some reason, windows won't allow me to shrink my internal hard drive more than 600 MB, so i couldn't make a usable partition for Ubuntu. Some other Dell users have had the same problem, so i decided just to use an External SATA drive. 

true, humans should be able to control computers, but then there was Dell. haha.

---

### Post by SlickRick on 2010-02-14
I see what you mean. It depends on where you install GRUB which is the bootloader. If you just choose a normal install and put the entire OS on the eSATA then there shouldn't be any problems booting windows without it, since the install would not touch the internal HD. And that is your best bet as a first time install. Just select the correct drive and select to use entire disk. Presuming there is nothing on the eSATA that you don't want to loose. If that is the case, select the "use largest continuous space" option.

---

