---
title: "Running Two Identical Realtek Based USB WiFi Adapters..."
date: 2022-03-07
forum: Networking &amp; Wireless
---

### Post by morrownr on 2022-03-07
This is a somewhat technical question but there are some very knowledgeable people here so...

The problem: If a person wants to plug two usb wifi adapters with the same Realtek chipset into the same system... ex. rtl8812bu, what happens is one adapter works and the second does not. This works with adapters based on Mediatek chipsets. This is a Realtek specific problem.

What I know:

If the system is booted with one adapter in the system. The adapter works fine. Then if the second adapter is plugged in after system is booted, it will also work fine. The problem happens if both adapters are plugged in at boot.

I've been digging into things from udev to Network Manager. I wish I could find a simple way to delay the creation of the interface for the second adapter until after the system is fully booted.

Any ideas or pointers appreciated.

Regards

---

### Post by robertwk on 2022-03-14
When you plug them both in, do they register as separate wifi devices?

---

### Post by morrownr on 2022-03-20
> **robertwk said:**
> When you plug them both in, do they register as separate wifi devices?

Hi robertwk

Sorry for the slow reply. 

The answer is yes. The problem is that one interface is usable, the other is not. I suspect that the issue is with with the Realtek drivers. udev is able to bring interfaces of the same type up in parallel and it may be that Realtek does not account for this or test it.

If I start the system with only one adapter in the system, the single interface comes up fine and is usable. If I then plug the second, identical adapter, in, the second interface come up and is usable.

I'm looking for a good solution to delay one or both adapters from being processed until such time as I want it to happen and, of course, I want the second adapter to be processed with a delay.

I'm asking because often users of the Realtek drivers I have up in Github show up asking why this doesn't work. I haven't been able to figure out a suitable solution. This doesn't happen with Mediatek drivers so it is a Realtek specific problem.

Thanks for any help you can provide

Nick
guthub.com/morrownr

---

