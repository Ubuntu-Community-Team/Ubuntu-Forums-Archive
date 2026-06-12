---
title: "Cisco Aironet 350 Wifi card w/PCI Adapter"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by flbsd on 2007-09-12
I am using Feisty Fawn, V 7.04.  System does not appear to totally recognize subject card. It is referenced  by pccardctl and lspci does reference the PCI bridge card ( this is in a tower).  It does not appear in ifconfig or in the network administration window - only local and eth0.

I did not boot with the card in the adapter, and have not gone back to try that yet....I am using as live CD until I was sure all hardware would work.

Also nothing appears about this card in /etc/pcmcia/config.opts.  Saw in another post Googled that there were line descriptors for the card and a ending line .. bind "ath_pci" referenced as needed.  This was for another previous version though.

Probably this is a very obvious mistake on my part for you experienced  Ubuntu/Debian types, but alast I am only a lowly FreeBSD guy. :(

Thanks for any  pointers.

Rich

---

