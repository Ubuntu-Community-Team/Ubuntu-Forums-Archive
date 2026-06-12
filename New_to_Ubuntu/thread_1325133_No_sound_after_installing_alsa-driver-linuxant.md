---
title: "No sound after installing alsa-driver-linuxant"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by Epiclow on 2009-11-13
Hello,

I made a topic a while back about installing my agrsm modem.
Well I got fed up trying to install that modem so I got my Conexant modem and stuck it in my computer.

I went to Linuxants site and downloaded and installed the modem driver, it works great.
I'm typing this out in Ubuntu now thanks to that driver.

But for some reason I had to also download the alsa-driver-linuxant package, I have Ubuntu 8.04, so I had to.

I don't know why, it's a HSF modem, it don't have any sound ports on it for speakers.:lol:

But anyway, how can I get me sound back?
I ran the make, make install commands but I can't figure it out.

This is what comes back as my sound card when I run lspci -v:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Unknown device 2a02
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at e000 [size=256]
    I/O ports at e400 [size=64]
    Memory at e8181000 (32-bit, non-prefetchable) [size=512]
    Memory at e8182000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>


Can I just uninstall the alsa-base thing and reinstall it to go back to the original audio settings without losing my modem drivers or what do I have to do?

I really don't wanna email the people at Linuxant for support.

Thanks.

---

### Post by Epiclow on 2009-11-13
Nevermind

I fixed it!!

I uninstalled the alsa-driver-linuxant and the precompiled Linuxant driver for my kernel and downloaded the generic driver that does not need the alsa driver and installed that.

I was hpoing it wouldn't have any trouble making the module and it didn't thank God.

Ok you Moderators, Masters of the forums, you can lock this now.:)

---

