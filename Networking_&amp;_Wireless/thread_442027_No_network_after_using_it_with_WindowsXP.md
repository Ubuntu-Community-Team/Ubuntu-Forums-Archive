---
title: "No network after using it with WindowsXP"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by nignasi on 2007-05-13
Hi,
we have serveral dual (WindowsXP, Ubuntu) booting PCs in a laboratory. Some of these PCs have problems connecting to Internet with Ubuntu but just when them have been connected to Internet with WindowsXP.
I can solve the problem if I unplug every cable (power, ethernet, keyboard, mouse and display) from any PC and connect again. Then Ubuntu allows new connections to Internet.
Let me explai better:
If we use our PCs just with Ubuntu, everything works. We can connect to Internet, reboot and shutdown without any problem.
If we use our PCs with WindowsXP, use Internet and afterthat, reboot to use Ubuntu or poweroff and start again with Ubuntu, there is no connection to Internet although we don't see any error message and network interfaces are configured as before. In this situation we must disconnect all cables form our PC, connect again and restart with Ubuntu. Everything works again.

Do you know what could be the problem?

Ignasi

---

### Post by WinterWeaver on 2007-05-13
O.o

Wow, that's quite an impressive bug... lol

Well, personally I don't know networking that well, but I have one thought.

Is there by any chance a IP conflict with the Windows and Ubuntu boxes?

eg... 
PC1: Ubuntu IP - 10.0.0.5   --- Windows IP - 10.0.0.6
PC2: Ubuntu IP - 10.0.0.6   --- Windows IP - 10.0.0.7

IOW, if PC1 is running windows, then PC2, when booted into Ubuntu, cannot access the network because of a IP conflict.

Thats the only thing I can think of atm.

Hope it helps, and hopefully someone with more experience stumbles uppon your question ^_^

WW

---

### Post by nignasi on 2007-05-13
No, this is not our problem. Even without any other computer siwtched on the problem persists and
they have same IP configuration in windows and Linux.

It doesn't happen with all PCs in laboratory, just with 6 new PC's. Tomorrow I can attach more
information (lspci, dmesg, ...) about their configuration.

Ignasi

---

