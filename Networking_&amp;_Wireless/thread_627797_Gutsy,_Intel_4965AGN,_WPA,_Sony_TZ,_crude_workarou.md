---
title: "Gutsy, Intel 4965AGN, WPA, Sony TZ, crude workaround"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by lenticular on 2007-11-30
Back in September I bought a Sony TZ130 laptop.  Finding that Feisty did not support the Intel 4965 AGN wireless chipset, I wiped Vista away and installed pre-release versions of Gutsy.  When production Gutsy came out, I did a clean install. Though all versions, I found that my laptop refused to connect to my home WPA access point.  dmesg would sometimes talk about "privacy configuration mismatch" in which it looked as though the laptop was intentionally dropping the connection.  Sometimes, I could not see wireless at all.

Along the way I installed wicd (which never got past the "getting an IP" stage); tried to compile the latest intel drivers from the intellinux sources ( but got compilation errors no matter how much I fussed with it), and tried loading and unloading various modules.

What works for me now is turning on the laptop with the wireless switch set to "off."  Once I've booted into gutsy, I turn it on and it automatically connects to my home WPA access point.  I've also seen an end to the random disconnects (and subsequent refusals to connect) that were also an annoyance.

Someday this ought to be addressed with an update since the 4965 chipset is appearing in a lot of laptops.  For now, though, I'll live with the clunky solution.

-John

---

