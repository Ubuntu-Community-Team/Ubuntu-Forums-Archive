---
title: "BCM4318 chipset no longer works with kernel update"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by mlsquad on 2008-06-21
Kernel 2.6.22-15 just hit a few days ago.  After upgrading my wireless no longer worked.  Everything looked fine, but "iwlist scan" showed no results.  If I choose to boot with the 2.6.22-14 kernel then wireless works just fine.  Anyone know what changes where made in this kernel update that would cause this?
The following is the output of lspci | grep Wireless
```
$ lspci | grep Wireless
05:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by Ayuthia on 2008-06-21
Are  you using the bcm43xx driver (bcm43xx-fwcutter or enabling the Broadcom driver in the restricted drivers section)?  I did not see any changes made for this module in the kernel update info, but I just took a quick glance.

If you are using NDISwrapper, you might have to recompile it.

---

### Post by mlsquad on 2008-06-21
> **Ayuthia said:**
> Are  you using the bcm43xx driver (bcm43xx-fwcutter or enabling the Broadcom driver in the restricted drivers section)?  I did not see any changes made for this module in the kernel update info, but I just took a quick glance.

If you are using NDISwrapper, you might have to recompile it.

I am using the bcm43xx-fwcutter that is setup as part of the restricted drivers module upon first boot after install.

---

### Post by Mutant on 2008-06-23
Having the same problem, using the fwcutter driver. In the restricted drivers screen it shows up as not in use under the new kernel, but in use under the old kernel.

---

### Post by mlsquad on 2008-06-23
> **Mutant said:**
> Having the same problem, using the fwcutter driver. In the restricted drivers screen it shows up as not in use under the new kernel, but in use under the old kernel.

I have made up a bug report.  Could you post your information there.  [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/242031](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/242031)

---

