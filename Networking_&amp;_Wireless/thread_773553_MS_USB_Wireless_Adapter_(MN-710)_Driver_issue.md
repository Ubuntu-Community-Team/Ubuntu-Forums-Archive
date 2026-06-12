---
title: "MS USB Wireless Adapter (MN-710) Driver issue"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by xDarKnighTx on 2008-04-28
I just installed ubuntu 8.04 64-bit version, everything's running smoothly, but I could not get my Wifi adapter to work.

I googled around and found out about ndiswrapper. Got the latest version installed (after installing the build-essential package so I can compile ndiswrapper), and copied over the INF and SYS files over. Got the driver installed, and when doing "sudo ndiswrapper -l", I got the message saying the device is present (which I assume is good).

But that's as far as I have gone. Instructions from ndiswrapper page says I need to re-plug in the adapter and I should see the lights go on, but I didn't. I'm not sure if I'm missing any steps, but when I go into the Network settings, I do not see the Wifi. I see my two other wired ethernet listed, and a "loopback" (not sure what this is). But no Wifi.

Am I missing something? Am I doing something wrong?

---

### Post by xDarKnighTx on 2008-04-29
Ok, found the problem, it appears the driver I have is 32 bit, and because my kernel is 64 bit, its saying it is unsupported:

[  689.619791] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  689.619802] ndiswrapper (load_sys_files:210): couldn't prepare driverf 'mn710'
[  689.620078] ndiswrapper (load_wrap_driver:112): couldn't load driver mn710; check system log for messages from 'loadndisdriver'

Anyone have any idea where I can get the 64-bit version of this dirver (or know how to modify it so it works on 64-bit)?

---

