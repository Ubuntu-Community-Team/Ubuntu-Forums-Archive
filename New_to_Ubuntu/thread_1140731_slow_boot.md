---
title: "slow boot"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by garrettstarnes on 2009-04-27
I have read a lot of posts on slow boot times, but a lot of it is over my head.  Some folks are talking about bootchart?  Maybe someone can help me get this together.  I have a dell inspiron computer with  a core 2 duo processor and it is taking about 1 minute 45 seconds to boot up.  A lot of folks are saying that they are getting 20 second boot times.  Like I said, I have read MANY threads, but get lost trying to follow them.  I have followed the links that they give and everything.  Any help?  Thanks.

---

### Post by 123456789123456789123456 on 2009-04-27
Is this a new problem?  Were you running ubuntu on the machine before, and this just start?  Or is this the first time using ubuntu on the machine?

things that can effect boot time, is one, ram
how much ram does the machine have?
are you running ubuntu, or xubuntu, kubuntu?
note that Ubuntu, and kubuntu will run on 256mb ram, but very very slow.
the listing says that they require 384mb ram, this would make them run faster, for sure, but could also cause slow boot times.  I suggest that you at least have 512mb ram, that would get down to about 20-30 sec boot time.  Processor speed may also affect things, Ubuntu seems to love amd processors, it seems to have some lag time with intel chips.  This is an observation, and not nessarily supported by the rest of the community.

---

### Post by garrettstarnes on 2009-04-27
I have 1GB of ram, so I would think it is enough to get it up in at least a minute.  Also I am running Ubuntu 9.04.  I have had slow boots since I started with linux with ubuntu 7.10.  I have been trying to read others posts and find out how to speed things up for a while now.

---

### Post by 123456789123456789123456 on 2009-04-27
this may be a wild guess, but how much if any of the ram is shared by video card?  if you go get information of the system, by system monitor, it should tell you how much ram you have, I would hazard a guess, that it is not showing 1024mb ram, or 1gb.  probably somewhere around 950mb I would guess.  you are correct though, that should be more than enough memory for the computer to boot.  What is the swap file listed as?  If the computer is contacting the hard dist for any extended amout of time, it could signal a problem with the ram, and cause a long boot time.  I don't know much about the dell computer you have, do you know the speed of the ram?  I would expect longer boot times with PC133, or even DDR ram.  Faster boot times with DDR2, and extreamly fast boot with DDR3, which I doubt the computer uses DDR3 ram.
I'm assuming DDR ram,
in that case, the slowest boot time, under normal circomstances should be abour 45 seconds.
45 seconds to 1 min from time grub reports booting, till the desktop, completely loads and is ready for use., not including time to enter in username/password.

---

### Post by garrettstarnes on 2009-04-27
How do I look to see what type of ram I have?

---

### Post by lovinglinux on 2009-04-28
Please keep in mind that the 20 s boot time people are talking about is just to boot to your login screen, not to when everything is ready to use.

To check your boot time, install bootchart:

```
sudo apt-get install bootchart
```

Then reboot. A bootchart image will be saved automatically at /var/log/bootchart every time you boot.

---

### Post by 123456789123456789123456 on 2009-04-28
sometimes you can enter into bios, and it may tell you there.  For me being a computer tech, I usually open up the case itself, and look at the ram.
now from the boot time you stated, is that from GRUB boot, all they way till you use the desktop?

---

