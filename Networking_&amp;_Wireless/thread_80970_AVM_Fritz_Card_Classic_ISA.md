---
title: "AVM Fritz Card Classic ISA"
date: 2005-10-23
forum: Networking &amp; Wireless
---

### Post by Garfield79 on 2005-10-23
Hello,

I recently started to migrate my home server from SUSE Linux 8.0 to Ubuntu Breezy 5.10. Most of my hardware was recongnized correctly and was usable without reconfiguring anything! :) 

But I have one problem. I used to run a fax server based on Hylafax under SUSE. That used an AVM Fritz Card Classic (A1) ISA and the AVM Capi to send and receive faxes. 

Having installed Breezy I realized that a lot of AVM Cards are supported by the provided Capi but not the Fritz Card Classic. The Kernel module fcclassic.ko is missing and thus cannot be initalized. :( 

I downloaded the sourece package provided by AVM and installed the kernel headers. But when trying to compile the kernel module the make command fails givning in the attached error message.... :???: 

Has anyone managed to get this card work with Breezy? 

I don't really understand why this card is listed in the capi.conf but is not supported in opposition to the other ones given there. Is it maybe planned for a future release?

---

