---
title: "Slow to Boot"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by Rob 41 on 2010-08-31
[SIZE=3]***Hi******,have***[/SIZE]***[SIZE=3] just installed ubuntu 10.04,(have allways been a windows user)but so far i like ubuntu much better but am having a few problems booting,it seems to take a long time,i have changed the timer in grub to 3 seconds which is fine for me,but from then it takes ages to boot just a flashing curser,i looked into a few other sites to try to find out why it is taking so long to boot and one of the suggestons was to get the grub menu which i have but i do not know what any of it means[/SIZE]*** [SIZE=3]***so am attaching it here  and hope someone can tell me if there is anything wrong with it and how to repair,i have also disabled floppy and checked jumper settings,thanks in advance***[/SIZE]

---

### Post by PPPilot on 2010-08-31
First off, Welcome Aboard. 

Without knowing what hardware you are running etc. It will be hard to diagnose your problem. Also what do you mean by slow?? My machine is an old (11 years old) slow one and Lucid boots up in 49 seconds from hitting return in GRUB. You do not have to wait for the timer by the way. 

I would suggest going to The System Menu and select Preferences>Startup Applications. This give you a list of applications that run at startup. Uncheck the ones you do not need. On my box I do not have Bluetooth so I unchecked the "Bluetooth Manager". My machine does not use any proprietary hardware drivers so I unchecked "Check for New Hardware Drivers". There were several others that I unchecked. These are all applications that run before you see the final desktop so any you turn off will speed up your boot time. If you find out you have unchecked one that you really need simply reopen the Startup Applications as above and recheck the box you need.  Of course, you have to reboot for the changes to take effect. Hope this helps............

---

### Post by clhsharky on 2010-08-31
Rob 41

Try shutting off your IGP Intel graphic controller off in BIO's so it will load radeon card sooner.

Sharky

May be a conflict.

---

### Post by Rob 41 on 2010-09-01
[SIZE=3]Hi firstly thanks for the quick reply,[/SIZE]

[SIZE=3]Dell Dimension 8300
Intel Pentium 4 3.00ghz
Psu 550w
RAM 1500gb
Ati radeon 9200se graphics (8xAGP)

i have unchecked everything i dont need in startup,everything is ok in bios as clhsharky sugested so maybe it is normal,just thought it was slow but this is the first time on ubuntu so i don't know,do you think i should stick with ubuntu graphics drivers or install the propierty drivers,i have read on other posts that my graphics card is not to good on ubuntu,again thanks for your help :D
[/SIZE]

---

### Post by clhsharky on 2010-09-01
Rob 41

The default open source radeon driver is the correct driver for your card in lucid.
There are some config files and fresher OS stacks, to help but not for the inexperienced to play with. 
Learn your new OS and you'll find your way to them when ready.

Good luck and welcome to the forum.


Sharky

---

### Post by Rob 41 on 2010-09-01
[SIZE=3]will do and thanks again.[/SIZE]

---

