---
title: "4 gb RAM on Linux Server Kernle"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-03-24
Hi... i have 4 gigs of RAM and upgraded to a Linux Kernel Server.... and i still only see 3 gigs of RAM could some 1 help me please...
TYVM!!

        Ravernomina




P.S. Ubuntu 32 bit edition dell dimension 3100

---

### Post by linuxisevolution on 2009-03-24
> **Ravernomina said:**
> Hi... i have 4 gigs of RAM and upgraded to a Linux Kernel Server.... and i still only see 3 gigs of RAM could some 1 help me please...
TYVM!!

        Ravernomina




P.S. Ubuntu 32 bit edition dell dimension 3100

you need the 64bit to see all the ram.

The extra 1gig is still in use though, just not by the os. It can go towards your bus overhead or something like that.

---

### Post by Ravernomina on 2009-03-24
i tried 64 bit and the thing is i get the 2.9gb glitch :L

---

### Post by Rolcol on 2009-03-24
Hm... Are you sure you're booted with the server kernel?  Copy and paste the results of ```
uname -a
``` (I don't know the flag to only display the kernel.  -a displays **a**ll).

You may have to edit GRUB to boot the Server Kernel.  If you don't want to edit it manually, install the startup-manager package.

(32Bit with a PAE enabled kernel should work, as far as I know)

---

### Post by Ravernomina on 2009-03-24
results were

Linux edward-desktop 2.6.27-11-server #1 SMP Thu Jan 29 20:19:41 UTC 2009 i686 GNU/Linux

---

### Post by boof1988 on 2009-03-24
> **linuxisevolution said:**
> you need the 64bit to see all the ram.
<snip>

Not true...

See [PAE at Wiki](http://en.wikipedia.org/wiki/Physical_Address_Extension).

> **Ravernomina said:**
> Hi... i have 4 gigs of RAM and upgraded to a Linux Kernel Server.... and i still only see 3 gigs of RAM could some 1 help me please...
TYVM!!

        Ravernomina




P.S. Ubuntu 32 bit edition dell dimension 3100

If the server kernel provides the [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension) capability.  Does your hardware have to have pae capability as well?  This is something I don't know the answer to, but it may help with trying to figure out your problem.

---

### Post by Ravernomina on 2009-03-24
well the thing is idk if i can im running a p4 prescott if that helps anything :L

---

### Post by jerrrys on 2009-03-24
according to the specs listed on cnet, your mobo only supports 2 gig..

---

### Post by Ravernomina on 2009-03-24
yet i have 3 gigs shown and i called dell its says its the recommended :P

---

### Post by LowSky on 2009-03-24
> **Ravernomina said:**
> i tried 64 bit and the thing is i get the 2.9gb glitch :L

2.9? That isn't a glitch. 

32bit Ubuntu will natively see up to 3.2 of 4GB

64 or 32 Bit with PAE will see 4GB.

If it isn't seeing the full amount, its most likely a motherboard or BIOS issue.

---

### Post by Ravernomina on 2009-03-25
2.9 glitch in 64 bit meaning even if i go 64 bit it will only see 2.9 gigs still -.- in 32 bit it sees 3 gigs meaning in 32 bit i get more RAM

---

### Post by LowSky on 2009-03-25
> **Ravernomina said:**
> 2.9 glitch in 64 bit meaning even if i go 64 bit it will only see 2.9 gigs still -.- in 32 bit it sees 3 gigs meaning in 32 bit i get more RAM

No not exactly that 2.9 could really be 2.999

I have 4GB  RAM and its sees 3.9 GB of RAM, its just the way it maps it out. You still have the same amount of RAM.

Honestly I cant even use 4GB or even just 2GB for normal day stuff.
A little while back I posted A pic with me running like 18 Applications, including a HD rip of a Movie and the system was only using about 900MB of RAM and no SWAP space. Sure your old P4 might not be able to handle that much work but RAM wise I couldn't even fill it up.

Well I found the picture so there is proof

---

### Post by Ravernomina on 2009-03-25
my "old" p4 has 2 cores running at 2.8 ghz ea can run 64 bit and also can hyper-thread at max speeds -.-

also i used free -m and it showed that i only had 2.928 not 2.9999999

---

### Post by Ravernomina on 2009-03-25
bump

---

### Post by boof1988 on 2009-03-25
> **Ravernomina said:**
> bump

Please consider waiting ~24hr before bumping your thread.

---

### Post by LowSky on 2009-03-25
> **Ravernomina said:**
> my "old" p4 has 2 cores running at 2.8 ghz ea can run 64 bit and also can hyper-thread at max speeds -.-

also i used free -m and it showed that i only had 2.928 not 2.9999999


[http://asia.cnet.com/reviews/pcperipherals/0,39051163,39096664p,00.htm](http://asia.cnet.com/reviews/pcperipherals/0,39051163,39096664p,00.htm)
I just read this review of your PC, for a 3 year old PC it was a low end system even when you purchased it in 2006. The PC can only accept 2GB (2048MB)of RAM, somehow you are able to use more, but not all. You have a hardware limitation NOT a Linux OS Issue.

You P4 isnt a dual core chip, it shows two core because of the hyper Threading,which is two virtual processors running within one physical processor. My Intel Atom Netbook is the same way. Sorry buddy but you really have a single core processor.


I hate to dissapoint you but we cant solve your issue for you.
here is more info on your processor capabilities.
[http://processorfinder.intel.com/details.aspx?sSpec=SL7Z8](http://processorfinder.intel.com/details.aspx?sSpec=SL7Z8)
[http://en.wikipedia.org/wiki/Hyperthreading](http://en.wikipedia.org/wiki/Hyperthreading)

---

### Post by skymera on 2009-03-25
> **Ravernomina said:**
> my "old" p4 has 2 cores running at 2.8 ghz ea can run 64 bit and also can hyper-thread at max speeds -.-

also i used free -m and it showed that i only had 2.928 not 2.9999999

Just to clarify. Your P4 has ONE core that has hyperthreading, so it looks like 2.

@OP: If you're running 32bit, does your CPU support PAE?

---

### Post by Ravernomina on 2009-03-25
thats the problems idk o.o and actually it does have 2 cores :l i looked up what hyper-threading was its 2 cores that share the load as in 3 on second core 2 on one core  :l

---

### Post by skymera on 2009-03-26
> **Ravernomina said:**
> thats the problems idk o.o and actually it does have 2 cores :l i looked up what hyper-threading was its 2 cores that share the load as in 3 on second core 2 on one core  :l

It's one core that splits itself into two.
So it can accept two threads. That's what hyper-threading is.

There was never a 2 core Pentium4

---

### Post by Ravernomina on 2009-03-26
well w/e any way i get great spped and the best processor i ever used. any way i want to know hot to tell if its PEA inabled :l

---

### Post by LowSky on 2009-03-26
I guess We were not clear before
You cant use any more RAM then what you are using!!!!

Your Computer is limited to 2GB by the manufacturer. Clearly you can see the 2.9 by some grace of God. No matter what you do you will not be able to use 4GB of RAM with that machine.

[B]EDIT:
Read this, _STRAIGHT FROM DELL_, the computer only will accept a MAX of 2GB
[http://support.dell.com/support/edocs/systems/dim3100/en/sm/specs0.htm#wp1052310](http://support.dell.com/support/edocs/systems/dim3100/en/sm/specs0.htm#wp1052310)[/B]

---

### Post by CRIMPS on 2009-03-26
> **Ravernomina said:**
> well w/e any way i get great spped and the best processor i ever used. any way i want to know hot to tell if its PEA inabled :l

You aren't listening. LowSky's last post should be clear enough I hope.

---

### Post by ptg on 2009-06-03
Hi

I have the same problem: I have 4gb of ram and Ubuntu 9.04 (64 bit) displays only 2.9gb. The bios correctly displays 4096mb. The notebook is a toshiba a100 and it supports memory expansions to 4gb.
Any solution? I have already tried almost everything, i think! :)

---

### Post by Ravernomina on 2009-06-04
It does the same to me So basically the fool who says the "grace of god can only help me". Yea he is wrong i just flashed my BIOS and now i have my 4 gigs try doing a BIOS update

---

### Post by ptg on 2009-06-04
Thanks for your reply... however, my bios is updated to the last available bios (v 6.00) in toshiba site... guess I'll just have to wait for a new one but I suppose that will not happen... the last update was in 2007.

---

