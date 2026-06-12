---
title: "Cannot connect 2 out of 3 times I boot livedisk"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by goldfish2 on 2008-07-13
When I boot the livedisk, it frequently is unable to connect using DHCP or manual configuration.  If I reboot the computer, sometimes it will start working again, and I will be able to connect, and both DHCP and manual connection will work.

This issue has carried over into my installed system where it sometimes cannot connect (even to my router @ 192.168.0.1), so I have to reboot the computer.

This is specific to this computer, all others on my network work fine.  What kind of issue would trigger randomly like this?

Thanks
~GoldFish2

---

### Post by forger on 2008-07-13
It would help if you tried the latest ubuntu live cd, hardy heron 8.04**[COLOR="Red"].1[/COLOR]** - They say they fixed a lot of stuff

You could file a bug at:
[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Be sure to include the output of this commands (once you get the live cd working):
```
lsb_release -a
lspci -nnv
```

---

