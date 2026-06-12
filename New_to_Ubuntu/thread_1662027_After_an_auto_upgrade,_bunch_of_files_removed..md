---
title: "After an auto upgrade, bunch of files removed."
date: 2011-01-07
forum: New to Ubuntu
---

### Post by ridethestream on 2011-01-07
This kind of adverse effects happen a lot or did I something to trigger it?

I was building a Wacom packages under /tmp directory. There were two directories I made: linuxwacom and xf86-xorg ones.  In the meantime, the synaptic package manager or update manager was downloading packages and upgrading system. 

When I restarted, the GRUB menu two more items. I was little worry about it. I logged in 2.6.35-24-generic, which was upgraded one. Desktop icons were gone, completely clean. xorg.conf.d/ directory were gone also the two directories and files under /tmp directory vanished. 

Thanks in advance.

---

### Post by cariboo on 2011-01-07
Anything in /tmp, gets removed on a reboot. If you are going to build programs/packages, do it in your home directory not /tmp.

---

### Post by ridethestream on 2011-01-07
> **cariboo907 said:**
> Anything in /tmp, gets removed on a reboot. If you are going to build programs/packages, do it in your home directory not /tmp.

Thanks

---

