---
title: "NDISwrapper error."
date: 2005-06-08
forum: Networking &amp; Wireless
---

### Post by taking_the_music_back on 2005-06-08
Hello, All


While not totally new to linux, this is my first experience with Ubuntu, and my first experience with linux on laptops in general.

In order to get my broadcom internal wireless to work, I downloaded NDISwrapper, went to gateway.com/support to retrieve the .exe file that contains my driver, and then used ndiswrapper -i to install the exe.

I then used the ndiswrapper -m command, as I should.

when using the modprobe command, the error I receive is as folllows:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


I apologize if this is a simple fix, but this is my first time using said NDISwrapper program, and I'm hoping to get my wireless card to work so I can rid myself of windows.

any help is appreciated, and I thank you in advance.

---

### Post by az on 2005-06-08
Post the output of
sudo ndiswrapper -l

---

### Post by I3roknI3ottle on 2005-06-08
Im having the same error with NDiswrapper, cept mines when I type in "Sudo Modprobe NDISWRAPPER"

---

### Post by az on 2005-06-08
Ndiswrapper is two things.  It is the kernel module and the userspace tool.

The kernel module is already in the kernel ubuntu runs.  The userspace tool is in the ndiswrapper-utils package.

If you use an older version of ndiswrapper-utils to install the driver and try to load a newer ndiswrapper kernel module, you will get that error.

You must have matching versions of the ndiswrapper-utils and module.  Just use the ones that come with the distribution and do not download the source and compile it yourself.

Could that be your poblem?

Knowing the result of 
sudo ndiswrapper -l 

would be helpful.

---

### Post by taking_the_music_back on 2005-06-09
I think I've figured it out...

I was using the wrong .inf file, for one...

and now that I've found it...

I can't remove the alias directive to install the new driver for the ndiswrapper -m command...

I am positive this is the right .inf file, for once...

I use a broadcom built in wireless on my gateway m320 laptop.

The .inf file is bcmwl5.inf, or another one I found on my windows and copied, bcmwl5a.inf.

Like I said, if this is stupid newb question fodder, I apologize.  my working knowledge of windows drivers is poor, and my knowledge of linux even less, in terms of this.

any help is appreciated

---

