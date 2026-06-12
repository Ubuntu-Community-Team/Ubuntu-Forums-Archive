---
title: "Missing network connection"
date: 2015-10-09
forum: Networking &amp; Wireless
---

### Post by neoculture2 on 2015-10-09
I have a fileserver running Ubuntu 10.4 LTS - at some point overnight, the server stopped talking to the network via its wired interface. Please note that it was working the night before. I powered up its screen and saw a message saying that the OS was out of support and would no longer be supported (fair enough) and the network icon was greyed out with an exclamation mark next to it. When I click on it, it tells me there are no networks for it to connect to.

Followed the cables to the ethernet switch to find that as far as the switch is concerned there is a working interface connected to it (i.e. both LEDs lit indicating connection at 1Gb/s).

So what the heck happened? Has Ubuntu turned off my network because the OS is now out of support? I can't see any errors in the log files(but then again I am a neophyte when it come to trawling through the logs), Would upgrading to 12.4 LTS fix the problem?

Cheers.

---

### Post by michi1983 on 2015-10-09
Hi,

I really doubt that this has something to do with the abandon of support for 10.04 to be honest.
Apart from that, I would still recommend to upgrade to 12.04 or even 14.04.
But in order to do that, your network connection need to work of course.
Have you tried to reboot your machine and see if it fixes the problem?

---

### Post by neoculture2 on 2015-10-09
Rebooted several times. Ethernet Switch implies the hardware is OK (both LEDS lit) but "computer says no".

As far as upgrades, I have to do 10.4->12.04->14.04 as there is no direct 10.4->14.04 path. I have the "alternate" ISO image to upgrade the PC.  Now I'll just need to buy some blank CDs 'cause the motherboard's too old to boot from USB keys.  <sigh>

---

