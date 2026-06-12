---
title: "new build boot from optical drive hanging"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by goldenfleece on 2009-01-10
I'm absolutely new to Ubuntu but not to computer building.  My BIOS is set to boot from the optical drive but the install options hang when the kernel install is at 100%.  

I'm hoping to get to a prompt where I can format my HDD and partition it.

Any suggestions?

---

### Post by cariboo on 2009-01-10
When you boot from the LiveCD, whether you select either Try before Install, or Install you should boot to the Ubuntu desktop. If the boot hangs before getting to the desktop, try booting using safe graphics mode. To select safe graphics mode at the menu screen press F4 select safe graphics mode and continue. 

I can't offer much more help without knowing what hardware you are running.

Jim

---

### Post by goldenfleece on 2009-01-10
Thanks Jim.
I'll give it a try.

Hardware:
Intel desktop board D975XBX2
Intel Core 2 Duo 6600 2.4Ghz

Plextor optical DVDR 
Western Digital WD3200KS-OOP HDD
ATI graphics card - can't remember which one off hand

---

### Post by goldenfleece on 2009-01-10
No luck on the f4 safe graphics mode.

I should mention that I have a couple Gigs of RAM as well.

Let me know if you need the details on any particular hardware.

Thanks,
Goldenfleece

---

### Post by goldenfleece on 2009-01-11
I adjusted the bios config for the HDD so that it is manual and then set the type to SATA.  Once done, I rebooted and the install was successful!

---

