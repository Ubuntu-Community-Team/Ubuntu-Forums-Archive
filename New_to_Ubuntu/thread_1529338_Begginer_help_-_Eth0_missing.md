---
title: "Begginer help - Eth0 missing"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by Rack1600 on 2010-07-12
Hello,
This is my first post on here so be gentle.

I ran an auto-update tool on my Ubuntu 9.10 installation last week, but only shut down over the weekend, and this morning when I booted my laptop, I no longer had any network access - synergyc etc return Network is unreachable.  I use the wired ethernet.  Eth1 is there - my wifi - the only wifi access I have does not get me on my internal network where I want to be, but I can technically get internet/external access if I need to load some update.
 
So I was just after some help getting my wired network hardware up and running again.

PC is a Dell Vostro 1520 laptop.  Not sure on the make of the network phy, probably part of the chipset?

I've tried >>sudo ifconfig eth0 up
and that returns: 
SIOCSIFFLAGS: Cannot allocate Memory

Sounds like the hardware driver failed to load at boot, or was "updated" to something broken.

What should I try next?

TIA
Simon

---

### Post by Rack1600 on 2010-07-12
(PS ifconfig has no eth0 in it at all, just eth1 which is my wifi, and:

lo  Link encap:Local loopback
    inet addr: 127.0.0.1 Mask 255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING MTU:16436 Metric:1
    RX 4,0,0,0,0
    Tx 4,0,0,0,0
    0,0

---

### Post by diablo75 on 2010-07-12
Well short of thinking of something brilliant... I'd check to see if there is an older kernel available for you to boot into.  You can check by holding down SHIFT at boot to get your Grub2 menu to appear and look to see if a previous version is available.  I can't think of anything else to try.

---

### Post by Rack1600 on 2010-07-12
Oops... my bad.
I just went and had a look at this, there are several kernel options (I inherited the PC with ubuntu already on), I booted into a different kernel this morning because I went and got a coffee as it booted (normal windoze practice)

I assumed it was the updates.

With the same kernel I was using last week it works OK... Problem solved :)

---

### Post by Rack1600 on 2010-07-12
(Technically it would be good to know what is wrong with that other kernel, but I guess I will find that out as I install new ones)

---

