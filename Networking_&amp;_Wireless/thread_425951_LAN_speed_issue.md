---
title: "LAN speed issue"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by popsicle on 2007-04-28
Hi all,

I have an issue with local network speeds in feisty. I cannot seem to get more than 5MB/s transfer speed to any other machines. All other boxes on the LAN have ~10MB/s speeds as did this one before installing feisty. Note that I am using the onboard nvidia ethernet (nforce4 chipset). I have also tried an Intel NIC with the same results.

00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
05:06.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)

Any suggestions would be fantastic.

Cheers

---

### Post by tgalati4 on 2007-04-28
Try blacklisting ipv6 and run your tests.

Perhaps adding

blacklist ipv6

to /etc/modprobe.d/blacklist

and rebooting.  Then run your throughput tests.  What method are you using to measure throughput?

Good luck.

---

### Post by popsicle on 2007-04-28
Try blacklisting ipv6 and run your tests. 

Done, no change :(

I am using the Gnome system monitor to measure the speed.

---

### Post by tgalati4 on 2007-04-28
Could be a bad cable.  Try connecting and reconnecting.  Sometimes contact resistance will reduce the quality of the signal.  Try swapping cables or removing kinks and rerouting cables away from interference sources.  The ethernet protocol is robust but it handles interference by reducing speed.

Try booting with a Dapper Live CD and testing throughput.  If it's a Feisty issue, I can't think of a better way to isolate hardware from software.

There are TCP tuning parameters such as the size of the transmit and receive buffers and the maximum packet size.  I don't remember where they are located, but perhaps they were changed in your other machines for performance reasons, but Feisty uses a slower/safer default.

---

