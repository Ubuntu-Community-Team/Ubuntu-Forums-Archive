---
title: "Installing Problem with Dualboot"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by ManiacR on 2009-03-23
Hello everybody,
I'd like to put Ubuntu on my AMD Ahtlon 64 x2 5200+, but there are some problems.

First time I tryed to install it from my livecd, sent to me by canonical.
When i tryed booting up from the CD it fully loaded the loadbar, and then poof it reboots.
So then I tryed the install in Windows function.
Now it boots to the login screen, I get logged in, then again it reboots.

Anyone can help me please?

---

### Post by ManiacR on 2009-03-23
Anyone??? :(

---

### Post by fly-by-night on 2009-03-23
I'll do a bump for you...lol

I remember my friend had to enter some command at the boot screen (for his 64bit AMD).  That was however with Dapper 6.06, don't know if it's still like that with 8.10/8.04.

You obviously have the 64-bit version of Ubuntu so that can't be it...

[https://answers.launchpad.net/ubuntu/+question/6537](https://answers.launchpad.net/ubuntu/+question/6537)

This first reply to this post mentioned a command line to enter at the boot screen (if you manage to reach it).  I know it's old but it might help.

---

### Post by benhath on 2010-09-21
Hello, all. Just joined and this is my first post.

Same here with 1.04 using a Core 2 DUO E6600 with ALI chipset and Geoforce 9500 GT, 3GB of ram. Reboots at random times during installation, and, if it happens to get all the way through, reboots during a session, no warning, no message. Computer runs Vista Home perfectly, memtest is OK. Dual Boot config. Tried 32bit and 64 bit both, same result.

Tried 1.10 64 bit beta from iso file and same thing. 

Was successful on an AMD2400 processor at 2BG but the mb only handles 1gb of memory so is really slow. Any help really appreciated.

Ben


> **ManiacR said:**
> Hello everybody,
I'd like to put Ubuntu on my AMD Ahtlon 64 x2 5200+, but there are some problems.

First time I tryed to install it from my livecd, sent to me by canonical.
When i tryed booting up from the CD it fully loaded the loadbar, and then poof it reboots.
So then I tryed the install in Windows function.
Now it boots to the login screen, I get logged in, then again it reboots.

Anyone can help me please?

---

### Post by wilee-nilee on 2010-09-21
> **benhath said:**
> Hello, all. Just joined and this is my first post.

Welcome aboard matey;)

You might want to start your own thread though for the best response.

Have a good time.

---

### Post by benhath on 2010-09-22
Thank you. It appears I fixed my own problem. Following a suggestion referred to above, I turned off ACPI in the bios during installation. While poking around in bios-land I also disabled HPET and WDRT. Installation went smoothly, no reboots. However I had to turn back on ACPI so that the installation would run, but it has been stable since. Newer motherboards appear to introduce new stuff that one must always keep abreast of or suffer consequences. Now to search for solutions to network printer connection problems (keeps asking for password, when I'm giving the correct one...)...
Ben


> **wilee-nilee said:**
> Welcome aboard matey;)

You might want to start your own thread though for the best response.

Have a good time.

---

