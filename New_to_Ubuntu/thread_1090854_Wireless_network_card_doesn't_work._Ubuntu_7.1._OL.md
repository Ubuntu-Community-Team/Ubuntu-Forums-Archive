---
title: "Wireless network card doesn't work. Ubuntu 7.1. OLD laptop. Any advice?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by Clay8317 on 2009-03-08
I know that everyone starts by saying "I'm a TOTAL NOOB!", but if the show fits... 
I'm using an OLD laptop- And old IBM Thinkpad with 10 gig Hard drive, 128 MB RAM and a Pentium II processor (300 MHz) (you have my permission to laugh.) Yesterday I installed Ubuntu 7.1. (I couldn't get the most recent version to install.) It works and the machine runs as well as can be expected.

Problem: My only link to the internet is a Dynex 802.11g Enhanced Wireless G Notebook Card #P11827

But sinse installing Ubuntu, the card isn't doing anything.

I've tried to follow the trouble shooting guide in the help screen. It say to open device manager(System> Administration> Device Manager)

I go to System> Administration> And there is no Device manager.

I check to see if the device is on (Application> Accessories> Terminal) Then I typed "sudo lshw -C network"

It said "*-network DISABLED" then followed with lots of specs on the device.

I assume that since it says "disabled" then the device is off, but the trouble shooting guide does not say how to turn the device on. What am I missing here?
Please help. Thank you in advance!](*,)

---

### Post by yeats on 2009-03-08
My first thought is that you'll want to be using a supported edition of Ubuntu (7.10 is about to stop being supported).  Do you have regular Ethernet access?  Updating to Hardy Heron 8.04 LTS would be a snap.  I'm just thinking you probably wouldn't want to go to a lot of trouble just to have to do it all over again :-).

If you will, though, go ahead and open a terminal window and type:

```
lspci -v
```

which lists all of your computer hardware in verbose (-v) form.

---

### Post by Clay8317 on 2009-03-08
My plan is to upgrade as soon as I can get on the internet. Unfortunately, I don't have wired network port. (It has a PHONE JACK!) 

As for the terminal window thing- Here we go:

06:00.0 Network controler: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11 g Wireless LAN controller (rev 02)
     Subsystem: Belkin Unknown device 7d1a
     Flags: bus master, fast devsel, latency 64, IRQ 11
     Memory at 1c000000 (32-bit, non-prefetchable) [size=8K]

---

### Post by yeats on 2009-03-08
There are several Broadcom wireless postings where people give/receive advice about how to get it working.  Just search "broadcom" (or use Google with "broadcom ubuntu"). 

Good luck.

---

### Post by Clay8317 on 2009-03-08
I'll try that. Thanks!

---

