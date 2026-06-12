---
title: "Vectra VL420 NIC"
date: 2006-07-17
forum: Networking &amp; Wireless
---

### Post by F00lGoneMadd on 2006-07-17
I just resently installed Ubuntu on an HP Vectra VL420 and it doesn't seem to have picked up on the Intel onboard NIC. I haven't had much time to trouble shoot due to the wife, but should tonight. I was just seeing if any one had some suggestions before I start digging into the problem.

---

### Post by mips on 2006-07-18
first Identify the exact chipset used, **lspci **should do that.
Next verify that the correct module is being loaded for that chipset.
Check that you get an IP address via DHCP, alternatively try and configure it statically.
Try and ping your router
Try and ping the outside world

---

### Post by F00lGoneMadd on 2006-07-18
I tried everything but the module. It is weird it gets a link light and acts like the card is there, but I get know IP. It must be the module. I am still a little Linux rusty so I am probably going to have to brush up alittle. Thanks for pointing me in the right direction. Cheers!

---

### Post by mips on 2006-07-18
Would help if you posted some more info like the output of lspci etc. Maybe we can get that direction 100% ;)

---

### Post by F00lGoneMadd on 2006-07-18
Here is what I got with lspci for the Ethernet:

0000:02:08.0 Ethernet Controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03).

Thanks for the help.

---

