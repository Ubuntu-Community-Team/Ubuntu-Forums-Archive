---
title: "Problem with IPW2100"
date: 2004-10-29
forum: Networking &amp; Wireless
---

### Post by davmac on 2004-10-29
Folks,

I'm pretty new to linux in general and Ubuntu in particular and I'm having problems getting my wlan working. The machine is a Dell Inspiron 510m with the Intel PRO/Wireless 2100 3A.

The wireless device appears to be there when I "lspci" and show some info in "lsmod". It looks to be some problem allocating IRQ 7, judging from the output from "dmesg". Possibly related to the fact that my AC97 soundcard isn't working either?

Output from these three are attached.

A suggestions to help me get this working would be gratefully received.

Regards,

Dave MacLeod

---

### Post by davmac on 2004-10-29
I'll reply to my own question as I finally managed to find the answer on Bugzilla. All that was required was to add acpi_irq_isa=7 to the boot up parms in /boot/grub/menu.lst

...and here I am doing this over the wireless connection. Hurrah!

Cheers all,

Dave MacLeod

---

