---
title: "sudo hangs with sis163 wireless on AMD64"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by cov on 2008-06-17
Hi.

I have a dual boot AMD64 machine with Ubuntu 8.04 Hardy 64 on one partition and a Suse 10.3 32 bit install on another.

I am using a wireless USB adapter (branded by LG, but using the SiS163 chip).

Under the Suse system the wireless works flawlessly using ndiswrapper.

However, under Ubuntu the machine locks up after trying to sudo.

Dmesg and /var/log/messages seem to be okay, although there is something that says "waiting for wlan0".

I'm not at the machine now as I am at work but I will post fuller details when I can...

It may be an issue with the AMD64 version of the sis163 drivers. Has anyone has managed to get this to work?

---

