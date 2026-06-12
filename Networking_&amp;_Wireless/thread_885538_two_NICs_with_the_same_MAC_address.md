---
title: "two NICs with the same MAC address"
date: 2008-08-10
forum: Networking &amp; Wireless
---

### Post by tremby on 2008-08-10
hey folks. this isn't an Ubuntu question but i don't know where to ask...

will the world explode (or will things break) if i change my laptop's wired ethernet NIC MAC address to the same as its wireless one?

what i'm after is my router giving the laptop the same IP address regardless of connection method -- wifi or wired.

only one interface will be active at a time, but the router won't let me reserve the same particular IP for two separate MAC addresses.

i know i could probably just use a static IP, but i'd rather stick to DHCP if possible.

cheers

---

### Post by jimv on 2008-08-10
I think it would be fine.  Worst case scenario is that you change your NIC back to the default MAC.

---

### Post by tremby on 2008-08-10
it worked! excellent!

i used the command
sudo ifconfig eth0 hw ether [new mac address]

it complained the first time that the device was busy, so i disabled networking and ran it again, and that was that.

i can now switch between wifi and wired and my router gives me the same IP. lovely!

thanks for the reassurance that the world wouldn't end.

---

### Post by caljohnsmith on 2008-08-10
Just thought I'd mention that you most likely could just set up your NIC with a static IP (same one as your wireless card) and accomplish the same thing without changing your MAC address.

---

### Post by tremby on 2008-08-11
> **caljohnsmith said:**
> Just thought I'd mention that you most likely could just set up your NIC with a static IP (same one as your wireless card) and accomplish the same thing without changing your MAC address.

as i said in the OP. cheers though.

---

