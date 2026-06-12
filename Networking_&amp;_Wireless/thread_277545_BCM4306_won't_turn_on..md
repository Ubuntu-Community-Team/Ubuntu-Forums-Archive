---
title: "BCM4306 won't turn on."
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by Chua-Chua on 2006-10-14
Hello,

I have the eMachines m6809 and I got the wireless working.
However, my motherboard broke and I had it replaced with a new motherboard.
Now, I think they just put in a new m68xx motherboard and I flashed it with the BIOS  from eMachines' site for the m6805.

Now, I tried the same steps to install the NDIS wrapper and I didn't receive any errors. The problem is that the wireless card will not turn on when I press the FN+F2 (Wireless card hotkey).

I dual boot with Windows and the wireless card LED turns on if I press FN+F2 to turn it on/off.

Is there a way to turn on the wireless card using the command line instead?

I don't think the problem is with NDISWRAPPER because I didn't receive any errors and NDISWRAPPER reports that the hardware is present.

Here is the lspci output:
0000:00:0c.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

ndiswrapper -l:
Installed ndis drivers:
bcmwl5          driver present, hardware present

Any suggestions?

---

### Post by Chua-Chua on 2006-10-15
Some progress:

I tried the hibernate function in my laptop, but the laptop freezes during the startup.

BUT, I noticed that the wireless card button did light up. 
I booted into Ubuntu normally, and the light will not turn on as before.

Could it be an ACPI problem?

Any help?

---

