---
title: "Memory ?"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by Frogs Hair on 2010-03-31
Hi,
Does the swap rate look right in relation to the amount of free memory my computer has ?

---

### Post by rossmoore on 2010-03-31
My thoughts are that you probably don't have enough swap to hibernate. I _think_ that when the system hibernates it writes the RAM to the swap partition. So typically you would try to have about twice your RAM as swap space. You have 256MB of swap and 2GB of RAM.

During normal operation you're unlikely to use all of that 2GB of RAM, so it probably won't be a problem - unless you do memory intensive stuff (run a big database, or web cache or something?).

When you say "swap rate", what do you mean exactly?

---

### Post by rossmoore on 2010-03-31
Oh, and swap does get used sometimes even though there's spare memory. Aside from executables, RAM gets used for disk caches and all sorts of other stuff that isn't necessary but does provide a performance boost. So stuff that hasn't been touched for a while can be swapped to disk to give the syste more RAM space to play in even though the applications aren't using much space up.

This setting can be controlled by something called "swappiness", which you can tweak if you really want to.

---

### Post by NightwishFan on 2010-03-31
That is too little swap if you would want to hibernate. The system should run fine though. I have disk space to spare so I have a good 5gb of swap, why not. A good swap is anything from 3/4ram to 1.5*ram.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Frogs Hair on 2010-03-31
> **rossmoore said:**
> My thoughts are that you probably don't have enough swap to hibernate. I _think_ that when the system hibernates it writes the RAM to the swap partition. So typically you would try to have about twice your RAM as swap space. You have 256MB of swap and 2GB of RAM.

During normal operation you're unlikely to use all of that 2GB of RAM, so it probably won't be a problem - unless you do memory intensive stuff (run a big database, or web cache or something?).

When you say "swap rate", what do you mean exactly?

I thought it seemed low . There was a thread  about swap thats what got me interested. I don't use the hibernate option , I have no reason to keep the computer running all the time. 


                                                                      Thanks !

---

### Post by Frogs Hair on 2010-03-31
> **rossmoore said:**
> My thoughts are that you probably don't have enough swap to hibernate. I _think_ that when the system hibernates it writes the RAM to the swap partition. So typically you would try to have about twice your RAM as swap space. You have 256MB of swap and 2GB of RAM.

During normal operation you're unlikely to use all of that 2GB of RAM, so it probably won't be a problem - unless you do memory intensive stuff (run a big database, or web cache or something?).

When you say "swap rate", what do you mean exactly?

Rate was the wrong word, Should I have more than I do ? and if so why not ?  I know windows only writes 
virtual memory if ram is low but I,m new to Ubuntu.

---

### Post by NightwishFan on 2010-03-31
I advise you to not add more 2gb RAM will be plenty. If by chance you ever reinstall, make it like 1-2gb swap though.

You can read the link above for some background info.

---

### Post by Frogs Hair on 2010-03-31
> **NightwishFan said:**
> I advise you to not add more 2gb RAM will be plenty. If by chance you ever reinstall, make it like 1-2gb swap though.

You can read the link above for some background info.

Thank you I added your link to my list.

---

### Post by 3rdalbum on 2010-03-31
You can't hibernate, but you can still suspend.

I have a desktop computer; instead of shutting it down I just suspend it. Suspend uses a little bit of power, but it's quicker to do and quicker to come out of than hibernation.

---

### Post by Frogs Hair on 2010-04-01
Thank For all your replies !!

---

### Post by no2498 on 2010-04-01
2 gigs is all i allow that = 2048

if i need more that that im doing something wrong

---

