---
title: "How to load network modules during installation"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by DaZjorz on 2005-07-16
Hello

I have a 3com network card in my server. The module for that is called 3c509 (well, thats the name on the SuSE cd). When I install, it tells me that no network cards were found.
Is there some guide that tells me how to load drivers during installation? I already tried starting the installation with
boot: # server insmod=3c509
but that didnt help. ](*,) 

Daz

---

### Post by DaZjorz on 2005-07-16
I did ALT+F2 and pressed ENTER then typed:
modprobe 3c509
and I guess it worked... it did not gave an error message but the light on the HUB is still off... I'll tell you if it worked. :)

EDIT: "Installing the Ubuntu base system..."

---

### Post by graza on 2005-07-18
hi, I have the same problem
both the motherboard's NIC and a second NIC (both 3c905) are recognised OK it seems (eg the PCI card is listed by lspci), yet I can't get them to work, which is a shame because everything else is running really well...
only lo is lited by ifconfig

I did try sudo modprobe 3c509 (same family as 3c905) 
but no luck...

The pci NIC came from an older linux machine, and so it has worked before

currently I'm not connectecd to a lan, as I'm waiting to get it installed. So, if a nic is in the pc, but not connected to a lan, would this explain why its not working (i wouldn't think so but getting bit fed up with this)  :| 

Any advice???
(i'm using kubunt 5.04)

Graza

---

