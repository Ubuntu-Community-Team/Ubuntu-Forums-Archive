---
title: "No wireless network - M1330"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by Z4ndX on 2008-08-30
Hi.. 
I know this is Ubuntu forum but i am desperate for help.

I'v just installed Debian Lenny and the only thing i cant get to work is the wireless part.

net applet wont show any networks when i click it. And yes, the it is enabled.

Whats wrong here ?

09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

---

### Post by pytheas22 on 2008-08-30
I don't know if Debian has *lshw* installed, but if it does, run:
```

lshw -C Network
```

to see if your wireless card is being claimed by any driver.  If not, you may need to compile the iwl4965 driver from [http://intellinuxwireless.org/](http://intellinuxwireless.org/)  I think the driver is in the kernel stack, so it should be in Lenny by default, but I could be wrong.

If iwl4965 is claiming your card but you still can't see networks, take a look at dmesg to see what it's saying about your card:
```

dmesg | grep -e iwl -e wlan
```

On Ubuntu at least, certain builds of iwl4965 tend to be buggy; if that's what's happening in your case, dmesg should mention some telling error messages.

Let me know if it helps.

---

### Post by Z4ndX on 2008-08-30
I found the problem.. i needed to install firmware-iwlwifi for it to work.

---

