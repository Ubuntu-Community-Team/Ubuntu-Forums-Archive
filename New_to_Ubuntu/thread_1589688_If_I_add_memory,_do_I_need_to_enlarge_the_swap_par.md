---
title: "If I add memory, do I need to enlarge the swap partition?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-10-06
Hello:

I bought 2 gigs of ram to add to the existing 4 gigs - do I need to increase the size of the swap partition?

If so, can this be done without harming my root and home partitions?

If so, how?

Thanks,

---

### Post by sxmaxchine on 2010-10-06
im pretty sure you could make your swap partition smaller, however i would just leave it as is

---

### Post by jtarin on 2010-10-06
No....in fact in some instances you can actually remove the swap partition. [The swap partition is virtual memory]("http://en.wikipedia.org/wiki/Swap_partition"). The more physical memory you add the less work your disk has to do.

---

### Post by sandyd on 2010-10-06
> **Robert.Thompson said:**
> Hello:

I bought 2 gigs of ram to add to the existing 4 gigs - do I need to increase the size of the swap partition?

If so, can this be done without harming my root and home partitions?

If so, how?

Thanks,
dependss on if you hibernate your computer.

---

### Post by snowpine on 2010-10-06
If you use the Hibernate feature, your swap must exceed your RAM. Otherwise, you may not even need swap at all, depending on your typical RAM usage.

---

### Post by t0p on 2010-10-06
> **Robert.Thompson said:**
> Hello:

I bought 2 gigs of ram to add to the existing 4 gigs - do I need to increase the size of the swap partition?

No.

---

### Post by pizza-is-good on 2010-10-06
Echoing the above posts.

If you plan to use Hibernate, then yes, you should increase Swap.
If you don't, then you do not need to do anything to it.

To increase it, you'll have to boot from a Live CD and use Gparted to shrink your Ubuntu Partition and enlarge Swap.

---

### Post by jtarin on 2010-10-06
[Make an informed decision based on your particular needs.]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Robert.Thompson on 2010-10-06
Thanks to all of you!:)

Just curious, is there a limit as to how much memory Ubuntu can use or needs?

---

### Post by NightwishFan on 2010-10-06
Ubuntu can probably use any realistic amount of memory on 64-bit or 32-bit with PAE. As for minimum requirements.. 512 is a solid number but you can get away with less, especially if you use xfce/lxde.

---

### Post by jtarin on 2010-10-06
Using 4GB or more of memory there have been reported gains using the PAE kernel rather than the generic.There is both 64 and 32 bit.

---

### Post by NightwishFan on 2010-10-06
> **jtarin said:**
> Using 4GB or more of memeory there have been reported gains using the PAE kernel rather than the generic.Ther is both 64 and 32 bit.

Which one?

---

### Post by jtarin on 2010-10-06
> **NightwishFan said:**
> Which one?Either one you want.....I don't know your system setup.....is it 64 bit or 32 bit?

---

