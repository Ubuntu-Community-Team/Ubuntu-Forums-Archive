---
title: "Atheros card stopped working"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by rafciu123 on 2007-02-11
Hi All,

I have problem with getting to work my wi fi card Ethernet controller: Atheros Communications, Inc AR500G 802.11abg NIC (rev 01). Following advice of one of community members I installed linux-restricted-modules and I was able to set up wireless network. 
Unfortunatelly after that I have changed repositeries source and updated my system /using synaptic I think/ and after next reboot I am not able to see any wireless cards installed:

iwconfig outputs:
lo no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

Also I don't see any wireless connections in GUI networking tool.
When I run synaptic it shows linux-restricted-modules to be installed.

I can't tell what tool I used for updating the system but it was one of GUI tools provided with Ubuntu 6.10. This tool downloaded some packages.


Please advice.

---

### Post by spd106 on 2007-02-12
Check that you have have the ath_pci.ko file in the /lib/modules/2.6.17-11-generic/madwifi/
 directory and ath_hal.mod.o file in the /lib/linux-restricted-modules/2.6.17-11-generic/ath_hal/
directory.

---

### Post by rafciu123 on 2007-02-12
I have linux-restricted-modules-2.6.17-10-generic installed but my kernell is 11. Can this be a reason why this card stopped working?

---

### Post by rafciu123 on 2007-02-12
I updated linux-restricted-modules to match my kernel version and it fixed the problem. 
Thanks for help.

---

