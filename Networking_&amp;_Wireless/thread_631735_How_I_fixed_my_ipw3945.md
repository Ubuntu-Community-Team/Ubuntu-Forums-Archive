---
title: "How I fixed my ipw3945"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Kleenux on 2007-12-04
Gutsy on my Dell laptop D630 - wireless **was** not working - Intel ipw3945

Possible source of the (ex)problem: installed Server then Desktop instead of Desktop (then servers)


After prevaricating for a while (3 days actually) and trying so many things (was finally on the way to reinstall the driver in the kernel) the ultimate answer came from nowhere, from a bug discussion actually, [here]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/134193")

This line from Tim Gardner was the solution:
[FONT="Courier New"]ipw3945 requires linux-restricted-modules-2.6.22 as well as linux-ubuntu-modules-2.6.22 to be installed.[/FONT]


Booting generic, a simple 
[FONT="Courier New"]apt-get install linux-ubuntu-modules-2.6.22-14-generic[/FONT]
followed by a reboot fixed the problem...

The golden line.

---

