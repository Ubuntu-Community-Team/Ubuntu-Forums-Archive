---
title: "memtest - in grub?"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by listerdl on 2010-08-11
Hi i have a dual boot with Windows 7 and Ubuntu.

The grub menu has a memtest which is listed as the last option in the grub boot options.

Does the memory test function refer to the ubuntu install only?

Thanks!

---

### Post by da burger on 2010-08-11
I believe (as the name suggests) that memtest is used for testing the RAM. It has nothing to do with operating systems.

Angus

---

### Post by listerdl on 2010-08-11
ah i see, so with a dual boot your machine would sort of share the available RAM and the memtest tests that openly available RAM which is used by both OSs?

---

### Post by bumanie on 2010-08-11
Memtest is a hardware test and thus OS and filesystem independent. Essentially tests RAM for errors.

---

### Post by listerdl on 2010-08-11
so basically RAM on a machine is shared by either OS in a dual boot environment?

---

### Post by da burger on 2010-08-11
It's not really shared. RAM is cleared every time you turn of the computer so it's not like an HDD. It's just that which ever OS that happens to be booted up at any given time will be using the whole RAM.

---

### Post by listerdl on 2010-08-11
ok but my real question is, if i run memtest from the grub menu on start up, which OS does it test? I have windows 7 and ubuntu installed, thanks

---

### Post by KdotJ on 2010-08-11
It doesn't test neither OS, it tests your RAM (your Random Access Memory). It has nothing to do with an OS at all

---

### Post by listerdl on 2010-08-11
So it RAM something that is made by the user or is it pre-installed?

---

### Post by da burger on 2010-08-12
RAM is hardware. It's not a program or an operating system, it's a physical part of your computer.

---

### Post by listerdl on 2010-08-12
so simply if I upgrade that hardware I upgrade the RAM right?

---

### Post by themusicalduck on 2010-08-12
Might be worth searching a bit about RAM and doing some reading up. Here is the wiki article on it to start: [http://en.wikipedia.org/wiki/Random_access_memory](http://en.wikipedia.org/wiki/Random_access_memory)

You can upgrade RAM quite easily. Particularly if you are using a desktop PC (it is possible in laptops too, but often more fiddly I think).

You can add RAM to your existing RAM if there is space on the motherboard, or replace the existing sticks with higher capacity RAM. You have to buy the right type of RAM though. e.g. my motherboard only supports DDR400 RAM.

---

### Post by TXpaniolo on 2010-08-12
The program memtest, if selected, will execute instead of any op sys and will run a repeating test on the RAM chips installed on your motherboard.  You can't run it from inside an op sys.  You run it for awhile, and if no errors are reported exit out and then choose an operating system to boot from.

---

### Post by Sikooz on 2010-09-19
Just wandering around...
So what is the real use of Memtest86, I guest that if something physical is happening to my ram, my pc will not boot at all? I'm I right? Therefore does this mean that my os can be using only part of my on board ram due to whatever problem?
thxxx a lot..

---

### Post by Paqman on 2010-09-19
Yes, the whole point of putting Memtest86 in the boot menu is to allow you to diagnose a problem with your RAM that might be preventing you from booting.

Ideally what you'd do is run Memtest for a while, and if it starts to spit out lots of errors, try pulling out the RAM sticks one by one and re-running Memtest to find out which one is faulty.

Note that faulty RAM won't always stop you from booting. It will also show up as random crashing and weird behaviour in your system.

---

