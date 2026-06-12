---
title: "ubuntu over XP"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by schleprock1967 on 2011-05-22
If I install Ubuntu over XP will I get a clean install, or will it try to keep my programs and files.
I just made an image of everything I need, however, I would like it if Ubuntu would try to just overwrite XP and keep the programs.

That is preferable by far.

Also, my XP is 32 bit and I want to go to 64 bit Ubuntu. The Windows 7 compatibility tool told me I would have to do a clean install to upgrade. That is why I am avoiding Windows 7 and looking at Ubuntu.

Are there options to expand my RAM and go from 32 bit to 64 bit that I am not considering?

Thank you for your consideration

---

### Post by Timmer1240 on 2011-05-22
windows software will not run on a Linux based system if you want to still use your windows applications it would be best to duel boot with Ubuntu

---

### Post by scott-ian on 2011-05-22
Linux uses a different file system, so it would have to overwrite the files.  You said "keep the programs," but Linux will not natively run Windows programs.  They are completely different OS's.  Does your computer have a 64 bit processor?  Please explain exactly what you are trying to do.

---

### Post by Timmer1240 on 2011-05-22
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) you may want to do some reading before jumping into the fire!

---

### Post by noidian on 2011-05-22
I presume your computer can support the 64 bit(amd64) (older PC's might be able to).

Windows programs don't natively run without reinstall on Ubuntu, though some can be made to run (in a toned down mode) using wine.

You might want to consider a dualboot.

Or if you really want to just get a feel of it try this
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Virtualbox you can install ubuntu and see if you like it(which you will) and try other OS as well...which is what I typically do.

Your RAM needs no upgrade typically ( Considering your able to run Win 7). It has no direct relation to 64bit. The 64bit corresponds to your processor instruction processing capability.

---

### Post by schleprock1967 on 2011-05-22
This machine is going to be taken off the front line. I was hoping to salvage it by giving it a 64 bit operating system and by adding more RAM. Maybe that could help me with some speed.

It is still a great machine. It just cannot perform at the level I want. So I can't play with a VM on it to see if I like it. Not enough horsepower.

It is a dual core 3.2 Ghz processors. Benchmarking software put it in the top 5 percent of all machines out there 3 or 4 years ago. (I can't even remember where I got the stats from.) So it isn't useless but, its glory days are gone.

How do I know if this thing has a 64 bit processor.

---

### Post by noidian on 2011-05-22
dual core 3.2Ghz is not all that bad. Sufficient to run virtualbox and play around. 

In Windows: go to system properties and check your processor specs. It will tell if your PC is 64. I believe Vista onwards has a feature which tells if your PC is capable of a 64bit upgrade. If so => you have a 64bit processor.

If using Ubuntu: lshw in command terminal

---

