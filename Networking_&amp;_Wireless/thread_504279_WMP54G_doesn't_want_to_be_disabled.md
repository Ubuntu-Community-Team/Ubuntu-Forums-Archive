---
title: "WMP54G doesn't want to be disabled"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by rusty2 on 2007-07-19
My little PCI friend the WMP54G resides on my PCI Bus.  I thought it was happy there.  It probably is too happy because in Kubuntu 7.04 when I disable it and the disabling is saved and I cold reboot, it's still shown as there and enabled.

Now, I know from other posts elsewhere, that there are a problem or two with 7.04 networking management, but I didn't realize that the coders had given the Linksys WMP54G a lease for life.   It comes up as eth1.  My mobo wired port is eth0;  the Belkin PCI wireless card using the ubiquitous Atheros chip is ath0,   

I had originally placed the WMP54G for wireless printing and the system does bring up a correct DHCP address, etc., but at this time I just merely want to disable it.

Any ideas, anyone?  Or is this operator error again?  Too simple a process,.....can't be.

---

### Post by kevdog on 2007-07-19
Can you post 
lshw -C network
so we can figure out the driver it is using.  After that its probably OK to blacklist the driver from there.

---

### Post by rusty2 on 2007-07-19
Hi;

I've never attached to a forum B4.  How does one do it?

BTW, I looked at the output in the terminal and it does show the WMP54G as disabled....it just doesn't show it in Knetworkmanager.   Oops!...just went back and looked at the network connections in 'Manual network configuration' icon and it is now disconnected.....I'm not pulling your leg...it never showed disconnected before.....

Anyway, just for kicks, tell me how to post the readout of the terminal...

Thanks

---

### Post by kevdog on 2007-07-19
Heard of cut and paste -- you can do that with terminal output.

---

