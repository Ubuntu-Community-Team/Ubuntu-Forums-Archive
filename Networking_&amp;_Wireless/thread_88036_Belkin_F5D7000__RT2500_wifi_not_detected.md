---
title: "Belkin F5D7000 / RT2500 wifi not detected"
date: 2005-11-09
forum: Networking &amp; Wireless
---

### Post by cheapskate on 2005-11-09
Hi

First off, let me say that I am very impressed with this forum. Everyone seems very helpful, which is why I am asking for help!

I have successfully loaded 5.10 onto my spare box but have some (not unexpectedly from reading these fora) issues with wifi.

I have a Belkin F5D7000 / RT2500 wifi card and it has not been detected properly.

It shows on Device Manager but not on Networking.

I RTFM'd the forum and tried sudo modprobe RT2500 and that seemed to work but iwconfig says no wireless extensions exist.

Given that R2500 is supposed to work out the box in 5.10 and that I am a Linux n00b, can anyone help me identify and resolve this rather niggling issue?

Thanks

CS

---

### Post by mips on 2005-11-10
Come right yet or still stuck ?

The other post on RT2500 were of no help ?

---

### Post by cheapskate on 2005-11-16
Hi

Thanks for replying. Not much progress yet as I have been busy but I did some digging on the Device Manager and realised that Ubuntu recognises the F5D7000 as a totally different device (in the say way as the F5D7010 is seen as something else). When I looked it up in the Ubuntu wifi compatibility forum, it indicated that I would have to go the Ndiswrapper route with the relevant driver. Shame really as I was hoping for pllug and play. Still, everything else worked. Being a lazy so and so, I may just but a wireless bridge and eth NIC and connect the box to the wifi network the hard way...

---

