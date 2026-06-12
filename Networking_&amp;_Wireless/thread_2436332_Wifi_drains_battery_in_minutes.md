---
title: "Wifi drains battery in minutes"
date: 2020-02-04
forum: Networking &amp; Wireless
---

### Post by triplemaya on 2020-02-04
Fully charged battery shows three hours or so of life. Connected by wire to the net it gives at least two hours of use. Connecting over wifi it is flat within five minutes or so. It charges up to full again quite quickly which seems to show that the wifi use is somehow interfering with the battery management rather than actually flattening the battery.

I have swapped out the battery for the one from another laptop and the problem is exactly the same, so not a battery problem.

I have performed a calibration which made no difference to the problem:

power-calibrate -R -r 20 -d 5 -s 21 -n 0 -p

I thought this was maybe a problem with the hardware, but fitted a spare hdd and installed a clean version of the os and this does not have the problem. So software / drivers is presumably the issue.

Running Ubuntu MATE 18.04

---

### Post by TheFu on 2020-02-04
Or the wifi card has a fault.  I would disable it in the BIOS and test using a USB wifi adaptor.

For wifi driver help, there's a sticky thread at the top of the wireless and networknig sub-forum.  Grab that script, run it and post the results.

---

