---
title: "No ATI driver after reboot (LiveUSB or Wubi-installed)"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by varghesejm on 2010-09-20
Hey everybody. I tried googling this and searching this forum to no avail.

I just recently started trialing Ubuntu. For some reason, on my Lenovo T400/WinXPSP3 machine, if I run a LiveUSB Ubuntu session or run the Wubi-installed version...whenever I reboot the machine to go back into Windows, I get a "No ATI driver installed..." message. My resolution is clearly all jacked and I have to proceed with installing the driver from scratch.

I can then reboot multiple times into windows over and over again, shut the machine down, bring it back up...and the video stays fine.

However if I startup with the LiveUSB Ubuntu or boot into Ubuntu and then reboot...the driver is gone again. VERY repeatable.

Any ideas?

Much thanks in advance! I'm very anxious to play more with Ubuntu but as of now, the driver issue is rather annoying.

---

### Post by sandyd on 2010-09-20
> **varghesejm said:**
> Hey everybody. I tried googling this and searching this forum to no avail.

I just recently started trialing Ubuntu. For some reason, on my Lenovo T400/WinXPSP3 machine, if I run a LiveUSB Ubuntu session or run the Wubi-installed version...whenever I reboot the machine to go back into Windows, I get a "No ATI driver installed..." message. My resolution is clearly all jacked and I have to proceed with installing the driver from scratch.

I can then reboot multiple times into windows over and over again, shut the machine down, bring it back up...and the video stays fine.

However if I startup with the LiveUSB Ubuntu or boot into Ubuntu and then reboot...the driver is gone again. VERY repeatable.

Any ideas?

Much thanks in advance! I'm very anxious to play more with Ubuntu but as of now, the driver issue is rather annoying.
have you checked windows disk for errors?

---

### Post by Mark Phelps on 2010-09-21
Saw a problem similar to this a while back where the person's machine had both onboard video and an ATI card, and they were dual-booting MS Windows and Ubuntu.  

Their problem was that when they rebooted, the BIOS defaulted to the first video option.  Thus, in Ubuntu, they were then using a different video option than they installed.

IF this is your situation, you will need to use the same video option in both MS Windows and Ubuntu -- and be sure that is the one set to default in your BIOS settings.

---

