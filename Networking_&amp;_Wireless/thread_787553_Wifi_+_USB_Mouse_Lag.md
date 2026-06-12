---
title: "Wifi + USB Mouse Lag"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by A.I. BOT on 2008-05-09
I use the RT2500 driver for my Belkin Wireless USB Dongle. What I have noticed is, when going to a website, when the browser is loading it, it lags my USB mouse, my mouse will jitter around the screen if I try to move it somewhere, it lags up.

Is this because so much data is being processed between the computer and the USB port my dongle is plugged into? which causes a delay in the processing of the port my USB mouse is plugged into?

Any solutions on this or is anyone having similar troubles?

Thanks.

---

### Post by A.I. BOT on 2008-05-11
Bump. Anyone have a fix or answer?

---

### Post by A.I. BOT on 2008-06-11
Bumping, again :)

---

### Post by the_aff on 2008-06-25
I have exactly the same issue with my wireless dongle, I thought it was a bug in Firefox 3 at first, so thanks for pointing me in the right direction.  I didn't really fix the problem, but worked around it with one of those USB to PS2 adaptors i had lying around.  But I'm sure someone will know a fix out there.

EDIT:  nope, thought i fixed it but the issue is still here.... read somewhere that it might be a nvidia driver issue.... still trying to find a solution..

---

### Post by the_aff on 2008-06-28
Ok finally fixed my issue, I tried installing new nvidia drivers but that didn't help.  It turned out to be the driver for my USB Wifi Dongle, I was using a TPLink WN321G.  Instead of using the default ubuntu drivers, I used the windows driver thru ndiswrapper... no more lag now :)

---

