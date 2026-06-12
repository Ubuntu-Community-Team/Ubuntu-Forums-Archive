---
title: "Ubuntu Classic session starts automatically after restart"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by ghoshankur.89 on 2011-06-26
Hi, I've recently started using Natty and my splash screen was giving problems. So i tried to stop it from loading by removing quiet splash from the /etc/default/grub file as suggested somewhere on these forums. That lead to Ubuntu being unable to start a normal Unity session and loading Ubuntu Classic instead after giving an error message about my graphic card.
So i changed the grub file back to original, and ran update-grub again. Now if i restart my computer, Ubuntu Classic session starts automatically. If i log out and log in again, Unity session comes up. I have set my default session to Ubuntu, but still after every restart it's Ubuntu Classic session

Just to be clear, this is what happens
1) switch on computer, weird black and white pattern instead of splash screen
2) on log in page, session selected is showing as Ubuntu
3) Enter password, Ubuntu Classic starts up
4) Log out, Log in again without changing any settings on startup screen
5) Unity Session starts

I'm okay with the splash screen, I just want to be able to load the normal Ubuntu session at start up

---

### Post by Gone fishing on 2011-06-26
I think yo'll find it's a graphic card / driver problem. What is your video card? 

sudo lshw will list the hardware.

---

### Post by ghoshankur.89 on 2011-06-27
description: VGA compatible controller
                product: RS690M [Radeon X1200 Series]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=64
                resources: irq:19 memory:c0000000-c7ffffff memory:d0400000-d040ffff ioport:4000(size=256) memory:d0500000-d05fffff

it was working fine before i messed with the grub file
thanks for the reply

---

