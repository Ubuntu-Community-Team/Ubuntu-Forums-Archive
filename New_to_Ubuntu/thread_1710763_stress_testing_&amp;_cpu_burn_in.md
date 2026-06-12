---
title: "stress testing &amp; cpu burn in"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by gregorymoore on 2011-03-20
hello all, i'm very new here and VERY new to Ubuntu. thank you in advance for this resource.

i'm building a new computer and i want to make sure everything is all set with the system before i dive in headlong. my overall plan for the computer is to dual boot ubuntu on one hard drive and then to boot OSX on another drive which will be my main OS. 

so, i plan on rigorously testing the system but i am finding it difficult to locate the best ubuntu stress testing software. i'm really green when it comes to linux so the easier the software is to use and navigate the better. 

i've read some stuff about running prime 95 through WINE but found nothing conclusive as to whether or not this works well.

i need to do all of the stress testing in ubuntu but i really have no idea where to start so any help or direction would be greatly appreciated. 

i also plan on running the 64 bit version of Ubuntu if that makes a difference, which it probably does.

---

### Post by kn0w-b1nary on 2011-03-20
Save a large file in a .tar.gz to stress test, though there are better tools to try, I just don't remember their names at the moment.

---

### Post by fabricator4 on 2011-03-20
One of the best things is still to run a good memory test program for an extended period.  memtest86+ is installed with Ubuntu now, so that you can boot straight into it through grub, but you can also get it on dedicated testing CDs like "The Ultimate Boot CD", which also contains other testing software for different systems and hardware.

Hardware testing is best done with dedicated software that has direct access to the hardware, rather than through a modern layered Kernel which does not provide this kind of access.

Chris.

---

### Post by kn0w-b1nary on 2011-03-20
+1 for the Ultimate Boot CD.

I've used UBCD a lot, so I heartily recommend it.

---

### Post by gregorymoore on 2011-03-20
> 

Hardware testing is best done with dedicated software that has direct access to the hardware, rather than through a modern layered Kernel which does not provide this kind of access.

Chris.


what kind of software would that be?



i'm definitely planning on using memtest.

---

### Post by gregorymoore on 2011-03-20
ok, i just started downloading "The Ultimate Boot CD" and that looks as though it should have everything i need to system check and burn in all my hardware unless there is other software somebody knows about but this looks pretty comprehensive.

thanks a lot guys!

---

### Post by kn0w-b1nary on 2011-03-20
You're welcome!

---

### Post by tgalati4 on 2011-03-20
sudo apt-get install cpuburn
man cpuburn
burnP6

Run burnP6 multiple times if you have dual-core processors:

burnP6 &
burnP6 &

Control-C to quit.

---

