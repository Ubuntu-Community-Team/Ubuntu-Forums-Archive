---
title: "MSI WIND Dual Monitor"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by manuleka on 2008-12-19
i'm running Ubuntu 8.10 on my Laptop and i can't figure out how to set my laptop screen as the default or primary monitor... everytime i plug in a monitor to my laptop the menu bars shift to the external monitor...

so when i disconnect it i have no menu bar unless i drag them into my laptop screen first

---

### Post by Hospadar on 2008-12-19
What video hardware does that little lappy have?

lspci
lshw

Might help you find out.  Post the output if you arn't sure.
Also take a look in System->Administration->Hardware Drivers and see if there are some restricted drivers available/installed for your machine.

---

### Post by manuleka on 2008-12-19
rt2860sta and the driver is enabled

---

### Post by Kareeser on 2008-12-19
Shooting out of the blue here, but:

On Intel cards, the VGA output is considered the primary monitor, always. It's a hardware restruction.

If the VGA monitor is absent (unplugged), then the menubars all shift to the LVDS output (Laptop screen).

Your MSI Wind may have the same setup.

Good laptop, btw :)

---

### Post by manuleka on 2008-12-19
> **Kareeser said:**
> Shooting out of the blue here, but:

On Intel cards, the VGA output is considered the primary monitor, always. It's a hardware restruction.

If the VGA monitor is absent (unplugged), then the menubars all shift to the LVDS output (Laptop screen).

Your MSI Wind may have the same setup.

Good laptop, btw :)

:) thanks... yea it's an awesome little puppy :)

came with Windows XP... i wiped it out with Ubuntu 8.10 and there's no turning back for me

---

