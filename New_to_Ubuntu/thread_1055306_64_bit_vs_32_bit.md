---
title: "64 bit vs 32 bit"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by darkH0rse on 2009-01-30
I am running a Compaq Presario SR1120NX with a Celeron D processor (i know, a bit old). When I try to install Ubuntu, i get the following error: "This kernel requires an x86-64 CPU, but only detected an i686 CPU. Unable to boot. Please use a kernel appropriate for your CPU." Is there any way that I can still install the 64 bit version, or will I have to settle for the 32 bit? I'm not sure if my computer supports 64 bit applications.

---

### Post by smothpocket on 2009-01-30
The Celeron D 330 which I believe is what you have is not a 64 bit cpu... therefore you can't install a 64 bit OS.

[http://www.intel.com/products/processor_number/chart/celeron_d.htm](http://www.intel.com/products/processor_number/chart/celeron_d.htm)

I wouldn't consider it settling for a 32bit OS as there would really be no advantage for you to run a 64 bit OS over a 32 bit in this case, and there are virtually no apps that run exclusively in a 64bit environment atm.

---

### Post by darkH0rse on 2009-01-30
oh well. thanks.

---

### Post by binbash on 2009-01-30
It is not 64 bit, just download and install 32bit version.

---

### Post by beastrace91 on 2009-01-30
> **smothpocket said:**
> 
I wouldn't consider it settling for a 32bit OS as there would really be no advantage for you to run a 64 bit OS over a 32 bit in this case,

Unless he has 4+ gigs of ram, which case you need a 64bit OS

~Jeff

---

### Post by Ayuthia on 2009-01-30
> **beastrace91 said:**
> Unless he has 4+ gigs of ram, which case you need a 64bit OS

~Jeff

Even if the original poster has 4+ Gb of RAM, they still cannot install the 64-bit OS (They need a 64-bit chip).  However, Linux kernels should be able to support 4+ Gb of RAM on the 32-bit.  I am not for sure if Ubuntu has enabled that option or not though.

---

### Post by bruce89 on 2009-01-30
> **smothpocket said:**
> I wouldn't consider it settling for a 32bit OS as there would really be no advantage for you to run a 64 bit OS over a 32 bit in this case, and there are virtually no apps that run exclusively in a 64bit environment atm.

That's not the case at all. All programs in the AMD64 port are compiled to use those 64 bits, and indeed have the extra registers and things like SSE2 enabled by default.

---

### Post by Maheriano on 2009-01-30
I have a follow up question. I installed 64 bit on my machine and then just followed the regular Add/Remove to put applications on there (Audacious, K3B, WINE, Apache2,....), how do I know they're running in 64 bit? Is it possible that things like my Firefox and Flash are running in 32 bit on my 64 bit machine? Should I be careful of this?

---

### Post by bruce89 on 2009-01-30
> **Maheriano said:**
> I have a follow up question. I installed 64 bit on my machine and then just followed the regular Add/Remove to put applications on there (Audacious, K3B, WINE, Apache2,....), how do I know they're running in 64 bit? Is it possible that things like my Firefox and Flash are running in 32 bit on my 64 bit machine? Should I be careful of this?

Everything is 64 bit. There are no issues, unless you like non-free things.

---

### Post by jerome1232 on 2009-01-30
I think all open source applications will be 64-bit. I know for fact flash (proprietary) is a 32-bit plugin with a wrapper that let's it work in a 64-bit browser. (There is actually a 64 bit version now but it's not ready yet imo, it kept crashing vuze when vuze tried to load a web page with flash content.)

On the whole, nearly everything in the repo's will actually be compiled for 64 bit.

---

### Post by smothpocket on 2009-01-30
> **jerome1232 said:**
> I think all open source applications will be 64-bit. I know for fact flash (proprietary) is a 32-bit plugin with a wrapper that let's it work in a 64-bit browser. (There is actually a 64 bit version now but it's not ready yet imo, it kept crashing vuze when vuze tried to load a web page with flash content.)

On the whole, nearly everything in the repo's will actually be compiled for 64 bit.

I know there were some issues with the wrapper using the 32 bit flash in  firefox 64... imo you get the best experience if you install the 32bit firefox as well

---

### Post by hyperhopper on 2009-01-30
i always thought that 32 bit systems maxed out at 3.2 something gigs of ram!

---

### Post by bruce89 on 2009-01-30
> **hyperhopper said:**
> i always thought that 32 bit systems maxed out at 3.2 something gigs of ram!

The 3GB thing is Windows's fault.

---

### Post by jerome1232 on 2009-01-30
I thought it was a hardware thing, 32 bit systems can address up to 4 GB's but some of the upper limits of that range is used to address other devices in the system. Since you have 4 GB's of ram some of the ram can't be addressed in favor of being able to address the devices on the system.

Also integrated video can take a sizeable chunk out of your ram but that's a whole seperate thing and will happen no matter how much ram you have and regardless if your using a 64 bit os or not.

---

### Post by smothpocket on 2009-01-30
"Linux

The Linux kernel includes full PAE support starting with version 2.6,[4] enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE. As of 2008[update], many common Linux distributions come with a PAE-enabled kernel as the distribution-specific default."

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by jerome1232 on 2009-01-30
Unfortunately for those that have 32 bit processors and >4gb's of ram that's not enabled on Ubuntu's generic kernel, only on the server kernel. They will have to compile their own kernel or sub-optimally use the server kernel to enable pae.

---

### Post by teh_yodeler on 2009-01-30
You can't install 64 bit ubuntu on that computer.

Download the 32 bit iso, burn it, try to install again

---

