---
title: "ath0 dissapeared"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by cap_gemo on 2006-12-15
Hi everyone,

  I'm having a big problem with my Ubuntu edgy now. My WLAN connection doesn't work anymore. It began several days ago. I use the WLAN connection in my University (FAU-Erlangen, Germany) and sometimes there are problems with the net, so I thought, that weren't my problems. But today I found out, that I don't have any ath0 device anymore! In "Network settings" I have only my eth0 and modem interfaces.

  Unfortunately I can't say, when it exactly hapenned. I know only that on the last day, when it was still working, I downloaded the new Linux kernel (2.6.19) from kernel.org, compiled (with old configuration) and installed it. But I don't think, this is the problem, because I have booted my old kernel (2.6.17-10-generic) and there was also no ath0 interface.

  What else have I done? Well, almost every day I make the updates by running apt-get update and apt-get upgrade.

  I know, it would be difficult to find out, what is the trouble here, but maybe someone has ideas.

  Thank you

---

### Post by ZERO_SHIFT on 2006-12-15
You may want to try Edgy Live CD and see if ath0 works there. If it does then I think an update you did may be the cause of the problem.

---

### Post by spd106 on 2006-12-15
Check that you have the linux-restricted-modules-2.6.17-10-generic package installed as that contains the madwifi driver for the ath0 device.

---

### Post by cap_gemo on 2006-12-15
> **ZERO_SHIFT said:**
> You may want to try Edgy Live CD and see if ath0 works there. If it does then I think an update you did may be the cause of the problem.

Yes, it works with Live CD. I'm not really sure (although it's of course stupid to be sure on non-sure for a Linux-newbie), that the update can cause this problem. Well, actually I made no update. I downloaded the 2.6.19 kernel source, copied the config of the 2.6.17-10 kernel and compiled the 2.6.19, making no change to the 2.6.17-10 kernel. I compiled the 2.6.19 kernel to a .deb package and installed it then. I didn't deinstall the old 2.6.17-10 kernel. And as I said, the WLAN doesn't work now also if I boot that old 2.16.17-10 kernel.


2 spd106: I have that package installed.

---

### Post by spd106 on 2006-12-15
You could try building the latest [madwifi]("http://madwifi.org") driver, then you'll also have the [security fix]("http://secunia.com/advisories/23277/")  we're all waiting for.

---

### Post by Dragonfire on 2006-12-15
This same problem has been experienced community wide with the TI 1410 and TI1400 series PCMCIA cardbus controllers. There was a larger update burst today aimed at resolving this issue. Though there are several groups still working to perfect a fix. from the information that has been gathered by the LCT, and NEOSA approximately 83% of those experiencing this problem first had it occuer 3 days ago after a major kernel update. Now 30% of those have run diagnostics checks only to reveal that some how the kernel update had rearranged the way the power distribution system worked momentarily, and had actually fried their pcmcia slots and/or cards.

---

### Post by cap_gemo on 2006-12-16
> **spd106 said:**
> You could try building the latest [madwifi]("http://madwifi.org") driver.

Thank you very much, I'll try to do it.

---

### Post by spd106 on 2006-12-16
> **Dragonfire said:**
>  Now 30% of those have run diagnostics checks only to reveal that some how the kernel update had rearranged the way the power distribution system worked momentarily, and had actually fried their pcmcia slots and/or cards.

Thanks for the info, though it's certainly not very reassuring.

---

