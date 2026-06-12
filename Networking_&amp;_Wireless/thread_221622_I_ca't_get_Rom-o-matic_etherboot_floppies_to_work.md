---
title: "I ca't get Rom-o-matic etherboot floppies to work"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by nwp2006 on 2006-07-23
Hi,

I've been trying to get LTSP working with limited success on Ubutu Dapper.  I have been able to get thin clients to boot when the network card supports it ( a friends laptop and some Dell optiplexes I was installing for a client), but never on the machines that I want to actually use for LTSP clients. 

I have a bin full of around 15 non-PXE network cards here and I've tried making floppy disks for all of them, but they never work.  I follow the instructions here: [https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe](https://help.ubuntu.com/community/UbuntuLTSP/LTSPBootingClientsWithoutPxe)

> Next select configure.

Make sure PXELOADER_KEEP_ALL is ticked, and it is a good idea to also tick POWERSAVE, ALLMULTI, MULTICAST_LEVEL1, MULTICAST_LEVEL2, and DOWNLOAD_PROTO_TFTM

When done, click get rom. 
 
But when the floppy boots it never gets past "Loading 192.168.3.253:/ltsp/pxelinux.0 ...."

Is anyone successfully making boot floppies for LTSP on computers without PXE nic cards?  Would I be better off just buying a bunch of network cards than wasting my time on this?](*,)

---

### Post by OMRebel on 2006-07-26
Were you able to get this to work?

---

