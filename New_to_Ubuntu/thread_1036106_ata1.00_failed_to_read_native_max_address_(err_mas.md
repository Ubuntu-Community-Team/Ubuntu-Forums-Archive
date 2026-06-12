---
title: "ata1.00: failed to read native max address (err_mask=0x4)"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by LordKthulhu on 2009-01-10
Hi folks - ran into a spot of trouble with Hardy. Following an update that required reboot (a while back), then-current kernel build refused to load up. Tried booting in recovery mode, got the message I do not remember at the moment (although I suspect it was the same as the one in the title). Changed Grub to boot an older kernel version and lived happily ever after - until today.

...fast forward to today. Same deal, did an update, kernel refused to boot normally or in recovery mode with this message: ata1.00: failed to read native max address (err_mask=0x4). Older kernels boot fine, newer - no-go (to be sure, the newest one never booted on this machine). What gives? Any ideas? Thanks! :confused: The hardware is a big silver box with thin TV :D (OK, it's actually Dell Inspiron 530, dual-boot with Vista, will post exact specs if needed). Thanks again.

---

### Post by LordKthulhu on 2009-01-10
Upgraded to 8.10, that seems to have fixed the problem. Still curious though, what gives? Ideas?

Thanks!

---

### Post by albinootje on 2009-01-10
> **LordKthulhu said:**
> Upgraded to 8.10, that seems to have fixed the problem. Still curious though, what gives? Ideas?

Thanks!

A search for :
> 
"failed to read native max address" (err_mask=0x4)

doesn't give that many hits.

This might be related :
[https://bugs.launchpad.net/ubuntu/+bug/107982](https://bugs.launchpad.net/ubuntu/+bug/107982)

---

### Post by LordKthulhu on 2009-01-10
Thanks, I found that one too. At this stage, naturally, the interest is academic, since that source seems to suggest that the bug was fixed in 8.10 - but I imagine it must not like the hardware.

---

### Post by JoshuaRL on 2009-01-10
> **LordKthulhu said:**
> Thanks, I found that one too. At this stage, naturally, the interest is academic, since that source seems to suggest that the bug was fixed in 8.10 - but I imagine it must not like the hardware.

Yeah, if your kernel wont boot, that is probably the issue.  Linux always has a little more problem with laptops anyway.  Well, except for my new Compaq Presario CQ60Z.  :)

She's pretty, and worked perfectly with a couple proprietary drivers.

---

### Post by albinootje on 2009-01-10
> **LordKthulhu said:**
> Thanks, I found that one too. At this stage, naturally, the interest is academic, since that source seems to suggest that the bug was fixed in 8.10 - but I imagine it must not like the hardware.

I tend to think that there are always several things to think about in these cases, like :

* BIOS bugs 
(Remember that BIOS software is usually compiled by Intel or ... Microsoft compilers [..shiver..]
* Kernel bugs
* Irq conflicts

It could be that a kernel bug was fixed, or that a kernel change made it work again.

If you really think that Linux doesn't like your hardware, then find out more details about your disk controllers and start searching for other postings with problems.
```

lspci

```

---

### Post by LordKthulhu on 2009-01-11
I think it was a reported bug for that kernel version, fixed in 8.10. Funnily enough, this is a desktop machine - never had that problem with either one of my laptops. Many thanks!

---

