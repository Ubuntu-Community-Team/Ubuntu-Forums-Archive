---
title: "libdnet changed MACs"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-07-21
I installed the "libdnet" package and it changed my NIC's MAC address. I remember the installer saying it was creating some files that would do so, but I figured it'd be easy to reverse the process. Unfortuantly, removing libdnet and restarting doesn't fix it and if I try to reinstall it, it downloads without giving me the helpful information screen. "whereis libdnet" didn't help either.

Anyone know how libdnet is changing the MAC addresses, and how to fix it?

---

### Post by djdicbob on 2007-07-21
Are you sure...I am not an libdnet expert but that MAC address change is software, the MAC address is in the hardware.  I am almost certain that this configuration is deliberate and maybe a normal operation.   Also, have a gander this way.....[http://libdnet.sourceforge.net/]("http://libdnet.sourceforge.net/"):mad:

---

### Post by B-Con on 2007-07-21
The *literal* MAC address can't be changed, but the *reported* MAC address is determined by the OS, and which MAC address the OS uses can be changed. libdnet apparantly decided to do that.

It's odd, because on my desktop libdnet didn't change anything, but it did on my laptop.

I looked at the website, but I think this was a Ubuntu-specific configuration. Could somebody trying installing libdnet and see if they get an ncurses-based blue screen? Go a couple screens into the process (don't complete it) and see what files it says will be added/modified.

---

