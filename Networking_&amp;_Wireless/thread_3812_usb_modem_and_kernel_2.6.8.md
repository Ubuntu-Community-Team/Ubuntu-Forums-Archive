---
title: "usb modem and kernel 2.6.8"
date: 2004-11-09
forum: Networking &amp; Wireless
---

### Post by astoltz on 2004-11-09
Greetings all,

I've just finished a fresh install of Warty and the only trouble I'm having is getting my USB modem to be recognized.  The modem uses the cdc_acm module, which, as far as I can tell, is getting loaded but udev doesn't assign a device (I was expecting to see /dev/ttyACM0 or something similar).  Sorry, I'm not sitting at the machine now so I can't get the dmesg output to attach but it definitely sees the modem and loads cdc_acm as the driver.  I'll mention that the modem was working fine on a Debian Sarge system with kernel 2.6.7.  

After some Googling, I'm starting to think that this is a kernel / module problem so my question is this:  Does anybody have a USB modem working under a 2.6.8 kernel?  Or maybe more specifically does anybody have a usb modem / cdc_acm module working in 2.6.8?  

Then, being new to Ununtu, will I have any problems if I compile my own 2.6.7 kernel (from kernel.org source) to see if that solves the problem?

Thanks,

  -Al

---

### Post by frank_iii on 2004-11-19
bump

Have you managed to get your USB modem recognized yet?  I've just installed ubuntu and, like you, cannot get a functional (under FreeBSD, NetBSD, and Debian Woody 2.4.x kernel) USB modem device to be detected.  I'd prefer not to build an older kernel but, if that's required, I'll do it...  ](*,)

---

### Post by jimbob@ubu on 2005-02-15
I installed a usb 2.6.10 kernel and the new initrd-tools  from the hoary repos and usb modem now works.

--
James

---

### Post by mattis on 2005-02-21
[QUOTE=jimbob@ubu]I installed a usb 2.6.10 kernel and the new initrd-tools  from the hoary repos and usb modem now works.

--
James[/QUOTE]

Hello,
I am new to this forum, but I have the same problem: the module for my elsa microlink 56k usb modem is not loaded.
Can you tell me where exactly I should look for this new usb-kernel. Should I just search for "usb" or "kernel" the next time I can use my apt-get in a lan?
greets
matthias

---

