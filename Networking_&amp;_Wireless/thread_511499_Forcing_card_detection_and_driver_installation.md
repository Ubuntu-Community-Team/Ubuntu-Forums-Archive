---
title: "Forcing card detection and driver installation"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by aminahmadi on 2007-07-27
Hi, 


I hope this is the right forum. 

I used my harddrive from another box in a new machine. It is a KDE on Ubuntu. It loads up andeverything is good. However I dropped in a new wireless card and refuses to acknoledge it and put the old one back and it is still not there. The onboard HP ethernet is also not detected. 

I need to know how to force this existing installtion to detect the new hardware and install the driver. I am used to Windows finding new things. 

How could I go about installing the wireless cards and the onboard Ethernet. 

The main Wireless card is a Dlink DWL-G520

the box is an HP Pavilion 7920. 


I can't reinstall because it gives a tty error thing and also some NTFS partition is supicously missing.

---

### Post by kevdog on 2007-07-27
Can you post the following -- this will tell us whether it truly does not recognize your card(s) or you are just missing a driver:

lspci -nn
lshw -C network

---

### Post by aminahmadi on 2007-07-31
Thanks.. 

I figured lspci was not listing the device, an IRQ conflict with the WL card. 

I unplugged that, and now LSPCI has it but still it is not one of the network devices.

---

### Post by aminahmadi on 2007-07-31
LSHW -C lists the card as
SMC2-1112TX and it notes is as UNCLAIMED. that would be the problem, 


how could I get some soul to claim this?

---

### Post by aminahmadi on 2007-07-31
so the card is an SMC2-1211TX

I need to add a module to be loaded to /etc/modules.conf?

and there is a related entry in /sbin/bus/pci/... but I don't know what to do with it. 
This tendency of unix OSes to see everything as a file confuse the hell out of me.

---

