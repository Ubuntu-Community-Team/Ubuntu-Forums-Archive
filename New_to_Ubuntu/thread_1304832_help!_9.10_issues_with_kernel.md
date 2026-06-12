---
title: "help! 9.10 issues with kernel"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by anico on 2009-10-29
just installed ubuntu 9.10.. i get errors in boot and sound problems.. but on top of that this error comes up.. 
i'm lost!
can anyone please help me??

---

### Post by jdrodrig on 2009-10-29
could you say abit about your machine hardware config?

---

### Post by matt082606 on 2009-10-29
Also what was your install method?  

Network upgrade, CD, etc.

---

### Post by anico on 2009-10-29
it's a sony vaio tz..installed it by burning the file to a cd like always.
Kernel 2.6.31-14
Grub 1.97~beta4      (i thought it was supposed to be grub 2.0 in 9.10??)

also i'm not too sure how to get the hardware specs in ubuntu :(

thanks a lot

---

### Post by ranch hand on 2009-10-29
The first thing to do is hit the button "report problem" and just follow the instructions as they come.

Secondly, open your terminal and run this command (just copy/past)
```

sudo dpkg --configure -a

```
Hopefully this will do nothing.  If something is stuck this should fix it.

Third, go to synaptic and hit "reload".  Go to the bottom left of the page and click on "status".

See if there is a listing for "broken packages".  If so report back here.

After the reload is done you may have some upgradeable stuff.  If you do not have any broken packages, hit "mark all updates" and then "apply".

See if this helps.

It would be nice if you would run;
```

uname -a

```
in terminal and post the results.

---

### Post by walt.smith1960 on 2009-10-30
the 32 bit RC and the AMD64 bit, both LiveCD's. Both machines have AMD processors, 1 32 bit and 1 64 bit.  I upgraded a 9.04 install running on the AMD single core 32 bit machine and saw the error message as well.  It occurred when awakening the system from suspend. I did some googling and found something about a timing issue. When a condition was not satisfied with 5 seconds after waking up, this error message would appear. Once that condition was satisfied the system was stable.  I did check for updates and downloaded a few. I haven't seen this message the last couple times I've unsuspended this machine to perhaps this problem is fixed. The system was never unstable to my knowledge.

With the LiveCD's the error from the 32 bit RC mentioned something about an ECC memory problem. This machine is a 64 bit AMD with 4 GB. DDR2 RAM.  That's not ECC as far as I know. I got the same message booting a 64 bit LiveCD downloaded today, Oct. 30.  I don't recall the contents of that message sent to the developers, sorry. I did downloaded a 32 bit .iso today and it boots fine, no error messages or problems. I'm not an IT pro and far less knowledgeable than many people on this forum but I have a good time with it:D.

Update:
I did an in place upgrade on an IBM ThinkPad R61 Jaunty to Karmic. No problems, no error messages. Smooth:D

---

