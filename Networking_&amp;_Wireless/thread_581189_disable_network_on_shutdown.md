---
title: "disable network on shutdown"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by dodoalien on 2007-10-19
hi

with 7.04 when i shutdown my notebook it uses to disable the ethernet card so the router led is off

now with 7.10 when i shutdown the notebook i see that the led of the ethernet link with notebook turns off and after the notebook shutdown the led turns on itself...

is like that the ethernet is still alive
how to turn it off?

---

### Post by Hero of Time on 2007-10-19
Have you changed any settings in your BIOS about Wake on Lan? Check that first. I run Gutsy too and my led goes off when my laptop is off.

---

### Post by dodoalien on 2007-10-19
no, nothing. i just updated to 7.10 from 7.04

---

### Post by dodoalien on 2007-10-20
i looked into BIOS and nothing is enabled about a wake-on-lan

the only thing that can be is
"Onboard LAN boot ROM" and is on "Disable"

got a dual boot here
Ubuntu7.10
WindowsXPhome

the led of the router, when i shutdown winXP, remains turned on too (but this is "normal", everd did that way with XP)

i dont know what to do... :/

this is annoying because if the led is turned on means thet my laptop is spending energy. while is turned off
:(

---

### Post by Hero of Time on 2007-10-20
If it already happened when Windows was shutdown, it isn't a Linux problem but a hardware problem. If you don't want your laptop to consume energy from your battery when turned off, remove the battery. That is a simple work-around. I advise you to check with your hardware supplier about this issue.

---

### Post by dodoalien on 2007-10-20
but it doesnt happen with 7.04

when i was on 7.04 the led was off on shutdown

---

### Post by dodoalien on 2007-10-26
i discovered that when i remove the energy adapter of the laptop, the LED of the ethernet on the router turns off and stays turned off when i insert the energy adapter...

i dont know why ... :)

---

### Post by glorfindel_i510 on 2008-02-28
Same thing happens to me. I've got a DualCore PC (not a laptop) and I recently discovered that when I shut down Gutsy the green led of the ethernet card does not turn off, nor does the led of my PC in the router. How can they be on when I have just turned off my computer???

My ethernet card is onboard, so I suppose that if this led is on, not only my ethernet card is on, but all my motherboard is consuming electricity. Why is it using electricity if I shutted down my PC????????????????????????

I checked if the same thing occured with XP....I'm sorry to say I'm pretty certain that this is an Ubuntu problem. When I shut down using XP everything is just fine.

---

