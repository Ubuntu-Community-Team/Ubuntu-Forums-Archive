---
title: "How to set up Wireless Internet from the beginning"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by honeybadgerman on 2009-03-17
I just installed ubuntu, hardy heron. i did not set up the internet when i installed. i want to know how to do so, as basic as possible. I will admit i am a noob, but at least i am a noob willing to learn.

the os does not seem to recognize my built in wireless card, which i know works.

---

### Post by LowSky on 2009-03-17
Please open a terminal

to do so go to Application> Accessories> Terminal
type this command

```
lspci -v
```

please copy the data it spews out to this thread.

Thank you this will identify the wifi chipset.

also you may need access to a wired connection if you have one availbe for the time being. so you can download and install the drivers

---

### Post by honeybadgerman on 2009-03-17
> ]02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver (rev 02)
        Subsystem: Dell Unknown device 0005
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at f8ffc000 (32-bit, non-prefetchable) [size=8K]


Edit bodhi.zazen: Eliminated the excess output and put it in a "quote" box ;)

---

### Post by bodhi.zazen on 2009-03-17
In general it either works or you need to do some extra work.

See here ;

[https://answers.launchpad.net/ubuntu/+question/62898](https://answers.launchpad.net/ubuntu/+question/62898)

Look at the last two posts.

---

### Post by honeybadgerman on 2009-03-17
ok, i looked at the last two posts. one has two links, the other is a long story.

should i download ndiswrapper on this computer, put it on a thumb drive, and move it over? the wired internet doesn't work either.

---

### Post by bodhi.zazen on 2009-03-17
Look at the "two links"

---

