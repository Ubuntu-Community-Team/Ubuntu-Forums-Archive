---
title: "Belkin 7010 works on kernel 15, but not 17..."
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by DJ Wings on 2007-02-13
Ladies and gentlemen, we have a problem. More accurately, I have a problem. Just like the last 2 times I've posted a help topic in the last few days. But this time, it's less serious. I have a Belkin F5D7010, which uses the MadWifi driver, along with an Atheros AR5211 chipset, to run. Okay, Ubuntu supports this, and it works fine whenever I boot into my shiny Edgy system with a 2.6.15-series kernel left over from my upgrade. But on the normal 2.6.17-series kernel, I get the following message:

wifi0: unknown hardware address type 801
:confused: 

I also tried rebuilding the MadWifi drivers on Debian Etch (kernel 2.6.18 ), and got the *same message*. I tried my Knoppix 5.0.1 live CD (kernel 2.6.17-RC), which has MadWifi built in, and got the *same message*.
:confused: 
Can anyone help me?

---

### Post by gradedcheese on 2007-02-14
you need to build the madwifi driver for your running kernel.  get the exact kernel name with "uname -r" and then apt-get install the kernel-headers package that corresponds (grab kernel-source while you're at it).  Then build the driver for that exact kernel, modprobe it and see if it works.

---

### Post by DJ Wings on 2007-02-14
Been there, done that. Doesn't work, same error.

---

### Post by DJ Wings on 2007-02-14
Bizarre update: It works on PCLinuxOS, kernel 2.6.17.14/Textstar, which uses DKMS for MadWifi. This is the only distro with a working MadWifi on 2.6.17 that I've tried.

---

### Post by spd106 on 2007-02-14
It sound like your card works with madwifi-old, but not madwifi-ng. 

Have you tried compiling madwifi-old on Edgy?

---

### Post by DJ Wings on 2007-03-04
It took me a while to get around to it, but yes, I did, and it returns the exact same error. Even weirder: the **splash** works on 2.6.15-23, but an upgrade to 2.6.15-28 later, it looks like a huge, pixellated, black-and-white blur. Same with 2.6.17-11.
I don't think upgrading to Feisty is going to be such a good idea...

---

