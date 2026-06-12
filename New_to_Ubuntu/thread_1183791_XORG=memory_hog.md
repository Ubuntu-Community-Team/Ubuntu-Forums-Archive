---
title: "XORG=memory hog"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by myolbug on 2009-06-10
okay I have an AMD 64x2 4400 on an MSI MObo with geforce 6100 256Mb onboard gpu and 3G RAM.  I am running 9.04.  
What I am noticing is that XORG starts using a lot of RAM if I leave my computer on for a while, without restarting, say two to three days.
The RAM usage goes up to about 500Mb or more and my computer seems a *little* slower, esp loading web pages.

Is this something that can be adjusted to have less RAM usage?  I am still learning what XORG does, so sorry if this is an obvious question.

---

### Post by cariboo on 2009-06-10
That is pretty normal ram usage, I have pretty much the same set up, but instead of using the onboard graphics adapter, I have a PCI-e 8400GS.

all the other specs are the same, MSI motherboard, 3Gb ram. running free gives me these results.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2984       1796       1187          0        118       1020
-/+ buffers/cache:        657       2326
Swap:         3812          0       3812
```

as you can see from the above output I'm using 657Mb of ram with just Firefox, Deluge, VirtualBox running.

---

### Post by jocko on 2009-06-10
> **myolbug said:**
> okay I have an AMD 64x2 4400 on an MSI MObo with geforce 6100 256Mb onboard gpu and 3G RAM.  I am running 9.04.  
What I am noticing is that XORG starts using a lot of RAM if I leave my computer on for a while, without restarting, say two to three days.
The RAM usage goes up to about 500Mb or more and my computer seems a *little* slower, esp loading web pages.

Is this something that can be adjusted to have less RAM usage?  I am still learning what XORG does, so sorry if this is an obvious question.
If you only use about 0.5 Gb out of the 3 Gb, you only use 17 % percent of your ram, so you should not see any slowdown at all.
It is possible that your computer swaps some of the data from ram to the hard disk's swap partition, which will cause a noticeable lag when the data is read back into ram. If you would do something to have less ram usage, you would force more swapping and see even more of a slowdown (ram is a LOT faster than your hard drive).
Check the output of running the command "free -m" in a terminal.

---

