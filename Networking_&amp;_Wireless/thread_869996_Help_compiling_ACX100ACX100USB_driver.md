---
title: "Help compiling ACX100/ACX100USB driver"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by realityisterror on 2008-07-25
Hello all,


I need to compile this driver and I'm following these instructions: [http://acx100.sourceforge.net/wiki/ACX](http://acx100.sourceforge.net/wiki/ACX)

I have the make, gcc, and build-essential packages.

When I run *sudo make -C /lib/modules/2.6.24-19-server/build M=`pwd`* from within the source directory, it tells me this:

```
make: Entering directory `/lib/modules/2.6.24-19-server/build`
make: *** No targets specified and no makefile found.  Stop.
make: Leaving directory `/lib/modules/2.6.24-19-server/build`
```


I'm 90% sure that I compiled the same drivers a few years ago on 6.06 Desktop and it worked for my stupid D-Link DWL-120+. All this trouble because I'm too cheap to go buy an ethernet card for this old PC...

Any suggestions are appreciated.

---

### Post by realityisterror on 2008-07-25
lsusb shows two different chipset IDs depending on what computer I use.

The computer that it works with gives 2001:3B00. (USB1.1)
The computer that doesn't gives 2001:3b01. (USB2)

Why is it doing this? I think for the few minutes the wireless was recognized, it recognized it as 2001:3b00 as well.

---

